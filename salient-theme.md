# Salient Theme Snippets

## Remove Header Padding Space on Mobile
There is an issue that some padding space is added to the top of a row on mobile (on the top row) for example, using a hero image woulsd look fine on a desktop but have padding space between it and the menu on mobile.  25px seems to work for me but it can be adjusted to suit

```css

@media only screen and (max-width:1000px){
#header-space { height: 25px !important} 
}
```

## CF7 Multi Column Form
This is the snippet for a repsonsive 2 column CF7 Form

### Form Code
```html
<div id="responsive-form" class="clearfix">
<h3>Enter Your Information to Register</h3>
<hr>
<div class="form-row">
<div class="column-half">First Name [text* first-name]</div>
<div class="column-half">Last Name [text* last-name]</div>
</div>

<div class="form-row">
<div class="column-full">Email [email* your-email]</div>

</div>

<div class="form-row">
<div class="column-half">Phone [text* your-phone]</div>
<div class="column-half">Postal Code[text* your-postal]</div>

</div>

<!--
<div class="form-row">
<div class="column-full">
<label for="community">Which Community?
<select name="community" id="community" required>
    <option value="" disabled selected>Select your option</option>
    <option value="1">Gallery Towns (Guelph)</option>
    <option value="23">Doon West (Kitchener)</option>
<option value="7">Usshers Creek (Ariss)</option>
<option value="22">Blackbridge Towns (Cambridge)</option>
<option value="8">Heritage Lane (Fergus)</option>
<option value="20">Mair Mills (Collingwood)</option>
</select>
</div>

</div> -->

<div class="form-row">
<div class="column-full">Are You Working With a Realtor?[checkbox your-realtor-choice label_first exclusive "NO " "YES"]</div>
<div class="column-full">[group realtor-group]Realtor's Name[text your-realtor][/group]</div>

</div>

<br />
<hr>

<div class="form-row">
<div class="column-half"><p class="tiny">Please confirm your interest in receiving emails from Granite Homes</p></div>
<div class="column-half">

[select* consent include_blank "YES" "NO"]
</div>
<div class="column-full">[submit "Send"]</div>
</div>

</div><!--end responsive-form-->
```

### CSS Code
```css


.wpcf7 .wpcf7-response-output {
    color: #000;
    margin: 15% 2% 15% 2%;
    font-size:24px;
}

.ascend .container-wrap input[type="submit"] {
    width:100%;
}


#responsive-form{
	max-width:900px /*-- change this to get your desired form width --*/;
	margin:0 auto;
        width:100%;
        
}
.form-row{
	width: 100%;
}
.column-half, .column-full{
	float: left;
	position: relative;
	padding: 0.65rem;
	width:100%;
	-webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box
}
.clearfix:after {
	content: "";
	display: table;
	clear: both;
}

select {
    font-size: 20px;
    
}

/**---------------- Media query ----------------**/
@media only screen and (min-width: 48em) { 
	.column-half{
		width: 50%;
	}
}
.wpcf7 input[type="text"], .wpcf7 input[type="email"], .wpcf7 textarea {
	width: 100%;
		background: #fff!important;
	padding: 8px;
	border: 1px solid #ccc;
	border-radius: 3px;
	-webkit-box-sizing: border-box;
	 -moz-box-sizing: border-box;
	      box-sizing: border-box;
	      background-color: #fff;
}
.wpcf7 input[type="text"]:focus{
	background: #fff;
}
.wpcf7-submit{
	float: right;
	background: #CA0002;
	color: #fff;
	text-transform: uppercase;
	border: none;
	padding: 8px 20px;
	cursor: pointer;
}
.wpcf7-submit:hover{
	background: #ff0000;
}
span.wpcf7-not-valid-tip{
	text-shadow: none;
	font-size: 12px;
	color: #fff;
	background: #333;
	padding: 5px;
	color: #000000!important;
    font-size: 16px;
}
div.wpcf7-validation-errors { 
	text-shadow: none;
	border: transparent;
	background: #f9cd00;
	padding: 5px;
	color: #9C6533;
	text-align: center;
	margin: 0;
	font-size: 12px;
}
div.wpcf7-mail-sent-ok{
	text-align: center;
	text-shadow: none;
	padding: 5px;
	font-size: 12px;
	background: #59a80f;
	border-color: #59a80f;
	color: #fff;
	margin: 0;
}
h3.refer {
    margin-top:50px;
}
.wpcf7-form {
    color: #333!important;

}
```

