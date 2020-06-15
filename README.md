# Email Boilerplate
A boilerplate used to create a basic email using html tables. The file index.html includes various layouts and options when creating an email. The file base.html is a stripped down template and can be used as a starting point. Here is an <a href="https://app.emailonacid.com/app/acidtest/ObKInOgLdiAk5lPB0mYZPGTNqCGhZJ903ZvEPbuKVypEK/list" target="blank">Email on Acid client summary</a> for the base email in this project 

<h3>Styles</h3>
```html
<style>

	// Since we are using th for the split columns we need to reset the font styles
  th { 
    font-weight: normal;
    text-align: left; 
  }

	// MOBILE STYLES: Adjust the max-width to match the width of the email

	@media screen and (max-width: 600px) {

		
		// adds 5% padding on either side of content that may have a fixed width on desktop
	    td.width5 {
	    	height:auto !important;
	    	width:5% !important; 
	    }

		// used to split columns on smaller devices
		// Do not use attribut selectors such as this: td[class=split]Gmail does not support attribute selectors and most pseudo-classes.
		// Using table headings for split columns works better then td for global support
	    th.split {
	    	float: left;
	    	height:auto !important;
	    	width:100% !important; 
	    }

		// split columns and add bottom border on smaller devices
	    th.split-border {
		    border-right: none !important;
		    border-bottom: 1px solid #ffffff !important;
	    	float: left;
	    	height:auto !important;
	    	width:100% !important; 
	    }

		// used to split columns and align center on smaller devices	
	    th.split-center {
	    	float: left;
	    	height:auto !important;
	    	text-align: center !important;
	    	width:100% !important; 
	    }

		// used to split columns and add spacing between columns on smaller devices	
	    th.split-spacer {
	    	float: left;
	    	font-size: 20px;
	    	height: 20px !important;
	    	line-height: 20px;
	    	width:100% !important; 
	    }
	}
	@media screen and (max-width: 650px) {

		// makes tables and images 100% width 
	    table[class=wrap100], img[class=wrap100] {
	    	height:auto !important;
	    	width:100% !important; 
	    }
	}

	// Links include Gmail and Apple attributes
  /* LINKS */
	/* Default link colors and attributes */
  p a,
  span a,
  u + #body span a:link, 
  u + #body span a:active, 
  u + #body p a, 
  u + #body p a:link, 
  u + #body p a:active,
  #MessageViewBody p a, 
  a[x-apple-data-detectors] {
    color:#141414 !important; 
    text-decoration:underline !important;
    font-weight: bold !important;
  }

	/* Secondary link colors and attributes */
  p a.link-white,
  span a.link-white,
  u + #body span a.link-white:link, 
  u + #body span a.link-white:active, 
  u + #body p a.link-white, 
  u + #body p a.link-white:link, 
  u + #body p a.link-white:active,
  #MessageViewBody p a.link-white, 
  span.link-white a[x-apple-data-detectors] {
    color:#ffffff !important; 
  }

</style>
```
<h3>Getting Started</h3>
<ul>
<li>Standard email width is 600px. The main email container should not exceed 640px to be to be viewed properly across all email clients.</li>
<li>Use tables and tables only! Divs are problematic and can create display errors in finicky email clients such as Outlook. Nested tables are used to create complex structures within a complicated layout.</li>
<li>Use inline CSS styles and keep it simple. Avoid shorthand css code and complex selectors!! This bloats your code and may cause erors and display issues in various email clients.</li>
<li>Do not use forms, javascript or flash ... if you are into that sort of thing :/ ... as they are not supported by email clients.</li>
<li>Do not embed video! Linked images or text links that direct the user to a hosted video is the best way to showcase video within an email. Embedded video is not supported by email clients.</li>
<li>Avoid the use of background images. The use of background images is not supported within all email clients. If you are going to use them, make sure you have a fallback and it is tested!</li>
	<li>
		Simple sematics count
		<ul>
			<li>Strong Tags are not supported by older email clients use the bold tag instead.</li>
			<li>Ordered and Unordered List Items aren't supported in all email clients. Use nested tables to accomplish this that include a bullet character for each point in the list instead. (See Lists Example Below) /li>
		</ul>
	</li>
<li>Test the email. It is a must to preview the coded email within all email clients before confidently sending out a campaign. <a href="https://www.emailonacid.com/" target="_blank">Email on ADid</a> and <a href="https://litmus.com/" target="_blank">Litmus</a> are a couple of great resources for this. </li>
</ul>

<h3>Content Blocks</h3>
Each content block has a column on either side with a width of 5%. This keeps the content from touching the edge of the table. 

Example:

```html
	<tr>
		<td>
			<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
				<tr>

					// Adding 5% padding on either side of the content block.

					<td width="40" class="width5">&nbsp;</td>
					<td>
						[ADD CONTENT HERE]
					</td>
					<td width="40" class="width5">&nbsp;</td>
				</tr>
			</table>
		</td>
	</tr>
```
<h3>Formatting Text and Links</h3>
Each sentence should be contained within it's own row. Addresses can be formatted with break tags. You can add .apple_link class to customize telephone number, address and location link colors for apple devices. 

Only basic, cross-platform fonts, such as Arial, Verdana, Georgia and Times New Roman, should be used when creating an email. Modern fonts can only be displayed using images which can get tricky since the image will be scaled down on smaller devices. This could make the image too small and render your text unreadable.

Example:

```html
	// Add font styles to <td> and paragraph styles to <p>.

	<tr>
		<td style="color:#141414; font-family:Arial, Helvetica, sans-serif; font-size:16px; font-weight:bold;">
			<p style="line-height:22px; margin:0;">[ADD CONTENT HERE]</p>
		</td>
	</tr>

	// Address formatted using <br />
	// Custom link color added for address on apple devices	using <span class="apple_link">

	<p style="line-height:16px; margin:0;"><span class="link-white">[ADDRESS LINE 1]<br />[ADDRESS LINE 2]</span></p>
```

<h3>Lists</h3>
Standard HTML lists don't render the same on all email clients. To combat this the use of nested tables is required. 

Example:

```html
	<tr>
		<td>
			<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
				<tr>
					<td>
						// Must use a nested table to avoid colspan issues
						<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
							// Adding valign="top" keeps the bullet at the top of the list item when it spans more than one line 
							<tr valign="top">
								// Bullet column - the use of image bullets is perfectly acceptable as long as you follow the image formatting rules
								// Adding width to bullet column for spacing between this and the list item
								<td width="10">&bull;</td>
								<td style="color:#141414; font-family:Arial, Helvetica, sans-serif; font-size:16px;">
									<p style="line-height:22px; margin:0;">Ultricies Dapibus Purus</p>
								</td>
							</tr>
						</table>
					</td>
				</tr>
				<tr><td height="5" style="font-size:5px; line-height:5px; mso-line-height-rule:exactly;">&nbsp;</td></tr> 
				<tr>
					<td>
						<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
							<tr valign="top">
								<td width="10">&bull;</td>
								<td style="color:#141414; font-family:Arial, Helvetica, sans-serif; font-size:16px;">
									<p style="line-height:22px; margin:0;">Ultricies Dapibus Purus</p>
								</td>
							</tr>
						</table>
					</td>
				</tr>
				<tr><td height="5" style="font-size:5px; line-height:5px; mso-line-height-rule:exactly;">&nbsp;</td></tr> 
				<tr>
					<td>
						<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
							<tr valign="top">
								<td width="10">&bull;</td>
								<td style="color:#141414; font-family:Arial, Helvetica, sans-serif; font-size:16px;">
									<p style="line-height:22px; margin:0;">Ultricies Dapibus Purus</p>
								</td>
							</tr>
						</table>
					</td>
				</tr>
			</table>
		</td>
	</tr>
```

<h3>Image Formatting</h3>
Remember, background images are not supported across all email clients. It is best to use images and text separately. 

When adding an image to an email it is important to assign specific style attributes to the image tags to maintain responsiveness. Adding .wrap100 will scale the image to be 100% width scaling nicely down to mobile. It is not necessary to add .wrap100 class to images smaller than the width of a mobile device. Doing so will stretch the image to be larger than it's natural dimensions. It is necessary to add a style attribute telling the image how to display. Without this the image may not display correctly in certain email clients. In that same manner the height and width of an image needs to be included.

Example:

```html
	// Add .wrap100 to scale images to be 100% with of the container
	// Add display:block, display:inline-block or float:left depending on your needs
	// Add height and width dimensions always
	
	<img class="wrap100" src="[IMAGE SOURCE HERE]" alt="[ALT TEXT HERE]" style="display:block;" border="0" height="300" width="650" />
```

<h3>HTML Buttons (not images)</h3>
HTML buttons do render a bit differently in each email client. The differences are minimal and this use is way better than using images. 

Example:

```html
<<<<<<< Updated upstream
  <tr>
    <td align="center">
      <div>
	<!--[if mso]>
	  <v:roundrect xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" href="http://litmus.com" style="height:37px;v-text-anchor:middle;width:146px;" arcsize="40%" strokecolor="#d31245" fillcolor="#ffffff">
	    <w:anchorlock/>
	    <center style="color:#d31425;font-family: Helvetica, Arial, sans-serif;font-size:14px;">FALLBACK</center>
	  </v:roundrect>
	<![endif]-->
	<a href="http://buttons.cm" style="background-color:#ffffff;border:1px solid #d31245;border-radius:30px;color:#d31245;display:inline-block;font-family: Helvetica, Arial, sans-serif;font-size:16px;line-height:44px;text-align:center;text-decoration:none;width:150px;-webkit-text-size-adjust:none;mso-hide:all;">BULLETPROOF</a>
      </div>
    </td>
  </tr>
=======

<td align="left">
	<!-- Bulletproof Button Outline (https://buttons.cm/). Update the button url and button text in both the [if mso]code snippet and the regular a tag. 
	-->
	<div><!--[if mso]>
		<v:roundrect xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" class="btn-outline" href="tel:5555555555" style="height:40px;v-text-anchor:middle;width:200px;" arcsize="86%" strokecolor="#ffffff" fillcolor="#00c3b4">
			<w:anchorlock/>
			<center style="color:#D31245;font-family:sans-serif;font-size:16px;font-weight:normal;">Bulletproff Button</center>
		</v:roundrect>
	<![endif]--><a class="btn-outline" href="tel:5555555555"
	style="background-color:#00c3b4;border:1px solid #00c3b4;border-radius:30px;color:#ffffff;display:inline-block;font-family:sans-serif;font-size:16px;font-weight:normal;line-height:40px;text-align:center;text-decoration:none;width:200px;-webkit-text-size-adjust:none;mso-hide:all;">Bulletproff Button</a></div>
	<!-- end bulletproof button -->
</td>
>>>>>>> Stashed changes
```

<h3>Spacing</h3>
Adding padding and margins within an email can be tricky. Some clients will render that spacing differently than others, and some not at all. It is best to take the time to add new rows with an assigned height or columns with an assigned width. This will cause some deep table nesting but it is fail proof. 

Example: 

```html
	
	<!-- HEADER IMAGE -->
	
	// Adding 35px spacer row beneath header image
	
	<tr>
		<td><img class="wrap100" src="[IMAGE SOURCE HERE]" alt="[ALT TEXT HERE]" style="display:block;" border="0" height="300" width="650" /></td>
	</tr>
	// spacer
	<tr><td height="35" style="font-size:35px; line-height:35px; mso-line-height-rule:exactly;">&nbsp;</td></tr>
	
	<!-- 2 COLUMNS -->
	
	<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
		<tr valign="top">	
			
			<!-- COLUMN 1 - NO BG COLOR / SPACER RIGHT -->
			
			// Adding 20px column spacer to right side of column 1
			
			<th class="split" width="50%">
				<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
					<tr>
						<td>[COLUMN BLOCK CONTENT HERE]</td>
						// spacer
						<td width="20">&nbsp;</td>
					</tr>
				</table>
			</th>
			
			<!-- COLUMN 2 - BG COLOR / SPACER LEFT AND RIGHT -->
			
			// Adding 20px column spacer to both sides of column 2
			
			<th class="split" style="background:#ebebeb;" width="50%">
				<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
					<tr>
						// spacer
						<td width="20">&nbsp;</td>
						<td>[COLUMN BLOCK CONTENT HERE]</td>
						// spacer
						<td width="20">&nbsp;</td>
					</tr>
				</table>
			</th>
		</tr>
	</table>
	
```

<h3>Splitting Columns</h3>
It is necessary to split columns on smaller devices so the content doesn't become squished and unreadable. It is best to use a table heading (th) instead of a table column (td) in this situation if you want the email to render properly in each email client. You can achieve this by adding the class .split to the table heading. Since email tags won't handle multiple classes various split classes have been created to accommodate the most common scenarios. 

Example:

```html
	<!-- DEFAULT SPLIT -->
	
	// Adding default .split class to make columns width: 100% @media screen and (max-width: 600px)
	
	<th class="split" width="50%">
		<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
			<tr>
				<td>[COLUMN BLOCK CONTENT HERE]</td>
				<td width="20">&nbsp;</td>
			</tr>
		</table>
	</th>
	
	<!-- SPLIT W BORDERS -->
	
	// Removing border-right and adding border bottom @media screen and (max-width: 600px) while maintaing default split styles
	
	<th class="split-border" width="33.3%" style="background:#333333; border-right:1px solid #fff;">
		<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
			<tr>
				<td width="20">&nbsp;</td>
				<td>[COLUMN BLOCK CONTENT HERE]</td>
				<td width="20">&nbsp;</td>
			</tr>
		</table>
	</th>
	
	<!-- SPLIT SPACER -->
	
	// Modifying column spacer to act like a row spacer under the first column @media screen and (max-width: 600px)
	
	<th class="split" width="50%">
		<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
			<tr>
				<td class="split">
					<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
						<tr>
							<td>[COLUMN BLOCK CONTENT HERE]</td>
						</tr> 
					</table>
				</td>
				// split spacer
				<td class="split-spacer" width="20">&nbsp;</td>
			</tr>
		</table>
	</th>
	<th class="split" width="50%">
		<table class="wrap100" align="center" border="0" cellpadding="0" cellspacing="0" width="100%">
			<tr>
				<td>[COLUMN BLOCK CONTENT HERE]</td>
			</tr>
		</table>
	</th>
```
