jQuery UI Triggered Autocomplete
====================

This widget lets you search for users to @mention in your posts.  It works very much like Facebook and Google+ in that it supports users with spaces in their name.  It writes to a hidden field with the user ID's formatted in this way: @[12345] while showing @username in the input box.  You can save the encoded string for easier parsing at display time.

```
$('#inputbox').triggeredAutocomplete({
	hidden: '#hidden_inputbox,
	source: "/search.php",
	trigger: "@",
	maxLength: 25
});
```

You can use a predefined array or json as a source.  Example json result:

```
[{"value":"1234","label":"Beef"},{"value":"98765","label":"Chicken"}]
```

To use the hidden field without an ajax call you need to pass an associative array:

```
$('#inputbox').triggeredAutocomplete({
	hidden: '#hidden_inputbox,
	source: new Array({ "value": "1234", "label": 'Geech'}, {"value": "5312", "label": "Marf"})
});
```

This also supports an optional img to appear beside each result.  You just need to pass an img URL for each value and label.  Here is the CSS for the image:

```
.ui-menu-item img { padding-right: 10px; width: 32px; height: 32px; }
.ui-menu-item span { color: #444; font-size: 12px; vertical-align: top }
```

If you want editable posts, you need to pass an id_map as an attr tag of the input box.  This is also json encoded and is simply an associative array of the included user_id => username pairs in the existing post. This is so when you change the post the original @mentions are preserved in their @[12345] format.

Demo: http://jsfiddle.net/vq6MH/146/

Discussion at Hawkee: http://www.hawkee.com/snippet/9391/