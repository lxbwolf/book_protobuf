This document provides a style guide for \`.proto\` files. By following these conventions, you'll make your protocol buffer message definitions and their corresponding classes consistent and easy to read.



\#\# Message And Field Names



Use CamelCase \(with an initial capital\) for message names – for example, \`SongServerRequest\`. Use underscore\_separated\_names for field names – for example, \`song\_name\`.



Using this naming convention for field names gives you accessors like the following:



&lt;pre class="prettyprint"&gt;&lt;div class="devsite-code-button-wrapper"&gt;&lt;div class="devsite-code-button gc-analytics-event material-icons devsite-dark-code-button" data-category="Site-Wide Custom Events" data-label="Dark Code Toggle" track-type="exampleCode" track-name="darkCodeToggle" data-tooltip-align="b,c" data-tooltip="深色代码主题" aria-label="深色代码主题" data-title="深色代码主题"&gt;&lt;/div&gt;&lt;div class="devsite-code-button gc-analytics-event material-icons devsite-click-to-copy-button" data-category="Site-Wide Custom Events" data-label="Click To Copy" track-type="exampleCode" track-name="clickToCopy" data-tooltip-align="b,c" data-tooltip="点击复制" aria-label="点击复制" data-title="点击复制"&gt;&lt;/div&gt;&lt;/div&gt;&lt;span class="pln"&gt;C&lt;/span&gt;&lt;span class="pun"&gt;++:&lt;/span&gt;&lt;span class="pln"&gt;

&nbsp; &lt;/span&gt;&lt;span class="kwd"&gt;const&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="kwd"&gt;string&lt;/span&gt;&lt;span class="pun"&gt;&amp;&lt;/span&gt;&lt;span class="pln"&gt; song\_name&lt;/span&gt;&lt;span class="pun"&gt;\(\)&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;{&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;...&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;}&lt;/span&gt;&lt;span class="pln"&gt;

&nbsp; &lt;/span&gt;&lt;span class="kwd"&gt;void&lt;/span&gt;&lt;span class="pln"&gt; set\_song\_name&lt;/span&gt;&lt;span class="pun"&gt;\(&lt;/span&gt;&lt;span class="kwd"&gt;const&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="kwd"&gt;string&lt;/span&gt;&lt;span class="pun"&gt;&amp;&lt;/span&gt;&lt;span class="pln"&gt; x&lt;/span&gt;&lt;span class="pun"&gt;\)&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;{&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;...&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;}&lt;/span&gt;&lt;span class="pln"&gt;



&lt;/span&gt;&lt;span class="typ"&gt;Java&lt;/span&gt;&lt;span class="pun"&gt;:&lt;/span&gt;&lt;span class="pln"&gt;

&nbsp; &lt;/span&gt;&lt;span class="kwd"&gt;public&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="typ"&gt;String&lt;/span&gt;&lt;span class="pln"&gt; getSongName&lt;/span&gt;&lt;span class="pun"&gt;\(\)&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;{&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;...&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;}&lt;/span&gt;&lt;span class="pln"&gt;

&nbsp; &lt;/span&gt;&lt;span class="kwd"&gt;public&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="typ"&gt;Builder&lt;/span&gt;&lt;span class="pln"&gt; setSongName&lt;/span&gt;&lt;span class="pun"&gt;\(&lt;/span&gt;&lt;span class="typ"&gt;String&lt;/span&gt;&lt;span class="pln"&gt; v&lt;/span&gt;&lt;span class="pun"&gt;\)&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;{&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;...&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;}&lt;/span&gt;&lt;/pre&gt;



\#\# \[\]\(\#top\_of\_page "返回页首"\)Enums



Use CamelCase \(with an initial capital\) for enum type names and CAPITALS\_WITH\_UNDERSCORES for value names:



&lt;pre class="prettyprint"&gt;&lt;div class="devsite-code-button-wrapper"&gt;&lt;div class="devsite-code-button gc-analytics-event material-icons devsite-dark-code-button" data-category="Site-Wide Custom Events" data-label="Dark Code Toggle" track-type="exampleCode" track-name="darkCodeToggle" data-tooltip-align="b,c" data-tooltip="深色代码主题" aria-label="深色代码主题" data-title="深色代码主题"&gt;&lt;/div&gt;&lt;div class="devsite-code-button gc-analytics-event material-icons devsite-click-to-copy-button" data-category="Site-Wide Custom Events" data-label="Click To Copy" track-type="exampleCode" track-name="clickToCopy" data-tooltip-align="b,c" data-tooltip="点击复制" aria-label="点击复制" data-title="点击复制"&gt;&lt;/div&gt;&lt;/div&gt;&lt;span class="kwd"&gt;enum&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="typ"&gt;Foo&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="pun"&gt;{&lt;/span&gt;&lt;span class="pln"&gt;

&nbsp; FIRST\_VALUE &lt;/span&gt;&lt;span class="pun"&gt;=&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="lit"&gt;0&lt;/span&gt;&lt;span class="pun"&gt;;&lt;/span&gt;&lt;span class="pln"&gt;

&nbsp; SECOND\_VALUE &lt;/span&gt;&lt;span class="pun"&gt;=&lt;/span&gt;&lt;span class="pln"&gt; &lt;/span&gt;&lt;span class="lit"&gt;1&lt;/span&gt;&lt;span class="pun"&gt;;&lt;/span&gt;&lt;span class="pln"&gt;

&lt;/span&gt;&lt;span class="pun"&gt;}&lt;/span&gt;&lt;/pre&gt;



Each enum value should end with a semicolon, not a comma.



\#\# \[\]\(\#top\_of\_page "返回页首"\)Services



If your \`.proto\` defines an RPC service, you should use CamelCase \(with an initial capital\) for both the service name and any RPC method names:



&lt;pre&gt;&lt;div class="devsite-code-button-wrapper"&gt;&lt;div class="devsite-code-button gc-analytics-event material-icons devsite-dark-code-button" data-category="Site-Wide Custom Events" data-label="Dark Code Toggle" track-type="exampleCode" track-name="darkCodeToggle" data-tooltip-align="b,c" data-tooltip="深色代码主题" aria-label="深色代码主题" data-title="深色代码主题"&gt;&lt;/div&gt;&lt;/div&gt;service FooService {

  rpc GetSomething\(FooRequest\) returns \(FooResponse\);

}&lt;/pre&gt;



  &lt;/div&gt;



&lt;div class="devsite-content-footer nocontent"&gt;



