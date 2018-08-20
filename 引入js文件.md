<h1><script>元素</h1>
	向HTML 页面中插入JavaScript 的主要方法，就是使用<script>元素。这个元素由Netscape 创造并在Netscape Navigator 2 中首先实现。后来，这个元素被加入到正式的HTML 规范中。HTML 4.01 为<script>定义了下列6 个属性。
	
	
<ul>
		<li><h3>1. async：</h3>可选。表示应该立即下载脚本，但不应妨碍页面中的其他操作，比如下载其他资源或
等待加载其他脚本。只对外部脚本文件有效。</li>
		<li><h3>2. charset：</h3>可选。表示通过src 属性指定的代码的字符集。由于大多数浏览器会忽略它的值，
因此这个属性很少有人用。</li>
		<li><h3>3. defer：</h3>可选。表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有
效。IE7 及更早版本对嵌入脚本也支持这个属性。</li>
		<li><h3>4. language：</h3>已废弃。原来用于表示编写代码使用的脚本语言（如JavaScript、JavaScript1.2
或VBScript）。大多数浏览器会忽略这个属性，因此也没有必要再用了。</li>
		<li><h3>5. src：</h3>可选。表示包含要执行代码的外部文件。</li>
  <li><h3>6. type：</h3>可选。可以看成是language 的替代属性；表示编写代码使用的脚本语言的内容类型（也称为MIME 类型）。虽然text/javascript 和text/ecmascript 都已经不被推荐使用，但人们一直以来使用的都还是text/javascript。实际上，服务器在传送JavaScript 文件时使用的MIME 类型通常是application/x–javascript，但在type 中设置这个值却可能导致脚本被忽略。另外，在非IE浏览器中还可以使用以下值：application/javascript 和application/ecmascript。考虑到约定俗成和最大限度的浏览器兼容性，目前type 属性的值依旧还是text/javascript。不过，这个属性并不是必需的，如果没有指定这个属性，则其默认值仍为text/javascript。</li>
</ul>

<h1>小结</h1>
	  把JavaScript 插入到HTML 页面中要使用<script>元素。使用这个元素可以把JavaScript 嵌入到HTML 页面中，让脚本与标记混合在一起；也可以包含外部的JavaScript 文件。而我们需要注意的地方有：<br>
	  在包含外部JavaScript 文件时，必须将src 属性设置为指向相应文件的URL。而这个文件既可以是与包含它的页面位于同一个服务器上的文件，也可以是其他任何域中的文件。<br>
	  所有<script>元素都会按照它们在页面中出现的先后顺序依次被解析。在不使用defer 和async 属性的情况下，只有在解析完前面<script>元素中的代码之后，才会开始解析后面<script>元素中的代码。<br>
	  由于浏览器会先解析完不使用defer 属性的<script>元素中的代码，然后再解析后面的内容，所以一般应该把<script>元素放在页面最后，即主要内容后面，</body>标签前面。<br>
	  使用defer 属性可以让脚本在文档完全呈现之后再执行。延迟脚本总是按照指定它们的顺序执行。<br>
	  使用async 属性可以表示当前脚本不必等待其他脚本，也不必阻塞文档呈现。不能保证异步脚本按照它们在页面中出现的顺序执行。<br>
	  另外，使用<noscript>元素可以指定在不支持脚本的浏览器中显示的替代内容。但在启用了脚本的情况下，浏览器不会显示<noscript>元素中的任何内容。
