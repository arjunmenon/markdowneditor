# markdowneditor
A very basic markdown based rich text editor.

#### Dependencies
Requires only jQuery and [microMarkdown Parser](http://simonwaldherr.github.io/micromarkdown.js/micromarkdown.js) *(weighs only 5kB)*

#### Usage
Include `<script src="markdown.js"></script>`

Initialize javascript
```
<script type="text/javascript">
	$(document).ready(function(){
	function myFunc(){
        var input = document.getElementById('input').value;
	    	var outputEle = document.getElementById('outEle');
		    outputEle.innerHTML = micromarkdown.parse(input);
    }       
    myFunc();

    var oldVal = "";
	$("#input").bind("blur keyup paste copy cut mouseup change", function() {
	    var currentVal = $(this).val();
	    if(currentVal == oldVal) {
	        return; //check to prevent multiple simultaneous triggers
	    }

	    oldVal = currentVal;
	    //action to be performed on textarea changed
	    myFunc();
	});
	});
</script>
```

Add HTML
```
<div class="md_editor">
  <a href="#insert_h1"         id="add_h1">         h1</a>
  <a href="#insert_h2"         id="add_h2">         h2</a>
  <a href="#insert_h3"         id="add_h3">         h3</a>
  <a href="#insert_h4"         id="add_h4">         h4</a>
  <a href="#insert_h5"         id="add_h5">         h5</a>
  <a href="#insert_h6"         id="add_h6">         h6</a>
  <a href="#insert_em"         id="add_em">         I</a>
  <a href="#insert_strong"     id="add_strong">     B</a>
  <a href="#insert_paragraf"   id="add_paragraph">  Para</a>
  <a href="#insert_blockquote" id="add_blockquote"> BQt</a>
  <a href="#insert_ul"         id="add_unord_list"> UL</a>
  <a href="#insert_ol"         id="add_ord_list">   OL</a>
  <a href="#insert_link"       id="add_link">       URL</a>
  <br />
  <textarea name="md_text_editor" rows="10" cols="50" id="input">Simple Markdown Editor</textarea>
</div>

<div id="outEle"> </div>
```


#### Goals
- Add image upload, table, font-selection, indentation, undo-redo controls
- Improve onChange text area behaviour. Currently if you select a control, the `outEle div` does not reflect the change on the fly. Have to focus out to view it.
- Bind Rich-text controls to ContentEditable
- Transform to a WYSIWYG-style editor


#### Notice

Since this is still a work in progress, lot of cool stuff is being worked upon. You can also work on this immediately. Just give a pull request. I would review and include your changes.
