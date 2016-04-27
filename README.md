﻿# digo-html-minifier
[digo](https://github.com/digojs/digo) 插件：使用 [html-minifier](https://github.com/kangax/html-minifier) 压缩 HTML。

## 安装
```bash
npm install digo-html-minifier -g
```

## 用法
### 压缩 HTML
```js
digo.src("*.htm", "*.html").pipe("digo-html-minifier");
```

### 源映射(Source Map)
本插件不支持生成源映射。

## 选项
```js
digo.src("*.htm", "*.html").pipe("digo-html-minifier", {
	caseSensitive: false, 	            	// 区分大小写。
	collapseBooleanAttributes: false,   	// 是否删除布尔型属性值。如 disabled="disabled" → disabled。
	collapseInlineTagWhitespace: false, 	// 删除内联(默认display:inline)标签中间的空白。仅当 collapseWhitespace=true 时有效。
	collapseWhitespace: true,               // 删除节点间的空白字符。
	conservativeCollapse: null,             // 是否在删除空白字符时保留一个空格。 仅当 collapseWhitespace=true 时有效。
	customAttrAssign: [],                   // 正则表达式数组，自定义属性赋值表达式。如 <div flex?="{{mode != cover}}"></div>。
	customAttrCollapse: null,               // 正则表达式，指定删除空行的属性。如 /ng-class/。
	customAttrSurround: [],                 // 正则表达式数组，包含自定义属性前后缀。 如 <input {{#if value}}checked="checked"{{/if}}>。
	customEventAttributes: [/^on[a-z]{3,}$/],  // 正则表达式数组，包含自定义事件属性。主要用于提取 JS 代码以压缩。 如 ng-click。
	decodeEntities: false,                  // 直接用法 Unicode 字符，而非转义字符。
	html5: true,                            // 根据 HTML5 规范解析文档。
	ignoreCustomComments: [/^!/],           // 正则表达式数组，匹配的注释将不被处理。
	ignoreCustomFragments: [/<%[\s\S]*?%>/, /<\?[\s\S]*?\?>/],  // 正则表达式数组，匹配的标签将不被处理。 (如 <?php ... ?>, {{ ... }}。
	includeAutoGeneratedTags: true,         // 插入 HTML 解析器自动生成的标签。
	keepClosingSlash: false,                // 保留自结束标签的 /。如 <link /> 中的 /。
	maxLineLength: null,                    // 指定压缩输出的最大行数。 代码会在标签位置自动换行。
	minifyCSS: false,                       // 是否压缩内联的 CSS (用法 clean-css)(可以是 true, Object 或 Function(text, inline))。*
	minifyJS: false,                        // 是否压缩内联的 JS (用法 UglifyJS) (可以是 true, Object 或 Function(text, inline))。*
	minifyURLs: false,                      // 是否压缩地址 (用法 relateurl)(可以是 true, Object 或 Function(text, inline))。
	preserveLineBreaks: false,              // 是否在删除空白字符时保留至少一个换行。 仅当 collapseWhitespace=true 时有效。
	preventAttributesEscaping: false,       // 禁止编码属性值。
	processConditionalComments: false,      // 处理条件注释。
	processScripts: [],                     // 包含脚本的 script type 类型。 如 text/ng-template, text/x-handlebars-template。
	quoteCharacter: '\'',                   // 属性名用法的默认引号(' 或 ")。
	removeAttributeQuotes: false,           // 删除 HTML 属性的引号，如果无法删除则不删除。
	removeComments: true,                   // 删除 HTML 注释。*
	removeEmptyAttributes: false,           // 删除只包含空白字符的属性。
	removeEmptyElements: false,             // 删除空元素。
	removeOptionalTags: false,              // 删除可选标签。
	removeRedundantAttributes: false,       // 删除默认属性值。
	removeScriptTypeAttributes: false,      // 删除 script 标签的 type="text/javascript" 属性，保留其它 type 类型。
	removeStyleLinkTypeAttributes: false,   // 删除 style 标签的 type="text/css" 属性，保留其它 type 类型。
	removeTagWhitespace: false,             // 删除属性之间的空白。注意这会导致生成非标准的 HTML。
	sortAttributes: false,                  // 根据用法频率对属性重新排序。
	sortClassName: false,                   // 根据用法频率对 class 名重新排序。
	useShortDoctype: false                  // 将 doctype 替换为 HTML5 的简短 doctype。
});
```
	
> *: 此选项已在插件内部自动设置。

另参考: [https://github.com/kangax/html-minifier](https://github.com/kangax/html-minifier)。
