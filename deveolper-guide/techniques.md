This page describes some commonly-used design patterns for dealing with Protocol Buffers.  You can also send design and usage questions to the \[Protocol Buffers discussion group\]\(http://groups.google.com/group/protobuf\).



\#\# \[\]\(\#top\_of\_page "返回页首"\)Streaming Multiple Messages



If you want to write multiple messages to a single file or stream, it is up to you to keep track of where one message ends and the next begins.  The Protocol Buffer wire format is not self-delimiting, so protocol buffer parsers cannot determine where a message ends on their own.  The easiest way to solve this problem is to write the size of each message before you write the message itself.  When you read the messages back in, you read the size, then read the bytes into a separate buffer, then parse from that buffer.  \(If you want to avoid copying bytes to a separate buffer, check out the \`CodedInputStream\` class \(in both C++ and Java\) which can be told to limit reads to a certain number of bytes.\)



\#\# \[\]\(\#top\_of\_page "返回页首"\)Large Data Sets



Protocol Buffers are not designed to handle large messages.  As a general rule of thumb, if you are dealing in messages larger than a megabyte each, it may be time to consider an alternate strategy.



That said, Protocol Buffers are great for handling individual messages \_within\_ a large data set.  Usually, large data sets are really just a collection of small pieces, where each small piece may be a structured piece of data.  Even though Protocol Buffers cannot handle the entire set at once, using Protocol Buffers to encode each piece greatly simplifies your problem:  now all you need is to handle a set of byte strings rather than a set of structures.



Protocol Buffers do not include any built-in support for large data sets because different situations call for different solutions.  Sometimes a simple list of records will do while other times you may want something more like a database.  Each solution should be developed as a separate library, so that only those who need it need to pay the costs.



\#\# \[\]\(\#top\_of\_page "返回页首"\)Self-describing Messages



Protocol Buffers do not contain descriptions of their own types.  Thus, given only a raw message without the corresponding \`.proto\` file defining its type, it is difficult to extract any useful data.



However, note that the contents of a .proto file can itself be represented using protocol buffers.  The file \`src/google/protobuf/descriptor.proto\` in the source code package defines the message types involved.  \`protoc\` can output a \`FileDescriptorSet\` – which represents a set of .proto files – using the \`--descriptor\_set\_out\` option.  With this, you could define a self-describing protocol message like so:



&lt;pre&gt;&lt;div class="devsite-code-button-wrapper"&gt;&lt;div class="devsite-code-button gc-analytics-event material-icons devsite-dark-code-button" data-category="Site-Wide Custom Events" data-label="Dark Code Toggle" track-type="exampleCode" track-name="darkCodeToggle" data-tooltip-align="b,c" data-tooltip="深色代码主题" aria-label="深色代码主题" data-title="深色代码主题"&gt;&lt;/div&gt;&lt;/div&gt;message SelfDescribingMessage {

  // Set of .proto files which define the type.

  required FileDescriptorSet proto\_files = 1;



  // Name of the message type.  Must be defined by one of the files in

  // proto\_files.

  required string type\_name = 2;



  // The message data.

  required bytes message\_data = 3;

}

&lt;/pre&gt;



By using classes like \`DynamicMessage\` \(available in C++ and Java\), you can then write tools which can manipulate \`SelfDescribingMessage\`s.



All that said, the reason that this functionality is not included in the Protocol Buffer library is because we have never had a use for it inside Google.



This technique requires support for \`proto2\` syntax \(as this is the syntax \`descriptor.proto\` uses\) as well as support for dynamic messages using descriptors. Please check that the platforms you need support these features before using self-describing messages.



&lt;/div&gt;

