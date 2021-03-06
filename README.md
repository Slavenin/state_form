state_form
==========

watch for form element state


EXAMPLE:
==========

simple:

```javascript
$(document).ready(function() {
	$('form').state_form();
});
```

with parametrs:

```javascript
$(document).ready(function() {
	$('form').state_form({
		//name input in form
		input_name: 'changed_state',  //is default
		//add input with changes in form
		insert_in_form: 1, //is defaul
		//function before form submit
		//call if form has changes
		if_changed: function() { //is default
			return true;
		},
		//field for excluded
		exclude: ['field1', 'field2'],
		//save hisory form states in local storage
		save_state_history: 1,
		//max count history snapshots
		state_history_length: 10,
		//name attribute with a unique value for the control
		controlling_attr: 'name'//is default,
		//selector for ignoring elements
		ignore: null,
		//call on add each elements
		onAddField: function(field) {console.log('element add')},
		//call on change elements
		onChange: function(field) {console.log('element changed')}
	});
});
```

PUBLIC METHODS:
==========

```javascript
//return true or false;
$('form').state_form('is_changed');

//return array with changes
$('form').state_form('get_changes');

//push snapshot curent state in history stack end
$('form').state_form('save_state');

//push snapshot curent state in history stack with key "key"
$('form').state_form('save_state', 'key');

//restore last saved form state
$('form').state_form('restore_state');

//restore saved form state by key
$('form').state_form('restore_state', 'key');

//return last saved history obj
$('form').state_form('get_history');

//return last saved history obj by key
//if key == 'state_form_all' return all history
$('form').state_form('get_history', 'key');

//return last form state by context
$('form').state_form('find_state');

//add field in controlling set
$('form').state_form('add_field', $(selector));

//remove field from controlling set
$('form').state_form('remove_field', $(selector));
```
