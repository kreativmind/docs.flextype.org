---
title: Html
---

- [\Flextype\Component\Html\Html](#class-flextypecomponenthtmlhtml)

<hr /><a id="class-flextypecomponenthtmlhtml"></a>
### Class: \Flextype\Component\Html\Html

| Visibility | Function |
|:-----------|:---------|
| public static | <strong>__callStatic(</strong><em>\string</em> <strong>$method</strong>, <em>array</em> <strong>$parameters</strong>)</strong> : <em>mixed</em><br /><em>Dynamically handle calls to custom macros.</em> |
| public static | <strong>anchor(</strong><em>\string</em> <strong>$title</strong>, <em>\string</em> <strong>$url=`''`</strong>, <em>array</em> <strong>$attributes=null</strong>)</strong> : <em>string</em><br /><em>Create HTML link anchor. echo Html::anchor('About', 'http://sitename.com/about');</em> |
| public static | <strong>arrow(</strong><em>\string</em> <strong>$direction</strong>)</strong> : <em>string</em><br /><em>Create an arrow echo Html::arrow('right');</em> |
| public static | <strong>attributes(</strong><em>array</em> <strong>$attributes=null</strong>)</strong> : <em>string</em><br /><em>Compiles an array of HTML attributes into an attribute string. Attributes will be sorted using Html::$attribute_order for consistency. echo '<div'.Html::attributes($attrs).'>'.$content.'</div>';</em> |
| public static | <strong>br(</strong><em>\integer</em> <strong>$num=1</strong>)</strong> : <em>string</em><br /><em>Create br tags echo Html::br(2);</em> |
| public static | <strong>doctype(</strong><em>\string</em> <strong>$type=`'html5'`</strong>)</strong> : <em>mixed</em><br /><em>Generate document type declarations echo Html::doctype('html5');</em> |
| public static | <strong>email(</strong><em>\string</em> <strong>$email</strong>)</strong> : <em>string</em><br /><em>Obfuscate an e-mail address to prevent spam-bots from sniffing it. echo Html::email('hello@flextype.org');</em> |
| public static | <strong>heading(</strong><em>\string</em> <strong>$title</strong>, <em>\integer</em> <strong>$h=1</strong>, <em>array</em> <strong>$attributes=null</strong>)</strong> : <em>string</em><br /><em>Create HTML <h> tag echo Html::heading('Title', 1);</em> |
| public static | <strong>image(</strong><em>\string</em> <strong>$file</strong>, <em>array</em> <strong>$attributes=null</strong>)</strong> : <em>string</em><br /><em>Create image echo Html::image('data/files/pic1.jpg');</em> |
| public static | <strong>macro(</strong><em>\string</em> <strong>$name</strong>, <em>\Flextype\Component\Html\Closure</em> <strong>$macro</strong>)</strong> : <em>void</em><br /><em>Registers a custom macro. // Registering a Html macro Html::macro('my_element', function() { return '<element id="flextype">'; }); // Calling a custom Html macro echo Html::my_element(); // Registering a Html macro with parameters Html::macro('my_element', function($id = '') { return '<element id="'.$id.'">'; }); // Calling a custom Html macro with parameters echo Html::my_element('flextype');</em> |
| public static | <strong>nbsp(</strong><em>\integer</em> <strong>$num=1</strong>)</strong> : <em>string</em><br /><em>Create &nbsp; echo Html::nbsp(2);</em> |
| public static | <strong>obfuscate(</strong><em>\string</em> <strong>$value</strong>)</strong> : <em>string</em><br /><em>Obfuscate a string to prevent spam-bots from sniffing it. This method obfuscate the value, randomly convert each letter to its entity or hexadecimal representation, keeping a bot from sniffing the randomly obfuscated letters. echo Html::obfuscate('hello@flextype.org');</em> |
| public static | <strong>toText(</strong><em>\string</em> <strong>$value</strong>, <em>\boolean</em> <strong>$double_encode=true</strong>)</strong> : <em>string</em><br /><em>Convert special characters to HTML entities. All untrusted content should be passed through this method to prevent XSS injections. echo Html::toText('test');</em> |
