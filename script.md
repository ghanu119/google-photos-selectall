# The below script will select all the videos and photos in google photos 

## You have to visit the photos.google.com
## Press `F12` 
## Find `console` tab from the new opened window

# Before script here is the code if you want to stop the selection process in between then use the below code:

```
clearInterval( timInterval );
```

## Suggestion: it is advisabel to stop the script whenever the selection reached to the 2000, because sometimes browser can not handle long process
## So, stop the process using the above line and then delete the process. And again press the below script and press ENTER

## Paste the below script to execute selection all the photos and press ENTER

```
var $viewEl = document.querySelector("c-wiz[jsrenderer][view]");
function selectAllPhotosClick () {
	var allCheckBox = document.querySelectorAll("div[jsaction][role=checkbox]");
	allCheckBox.forEach( d => { 
		var ariaLabel = d.getAttribute("aria-label");
		var isChecked = d.getAttribute("aria-checked") == 'true';
		if( !isChecked && !ariaLabel.toLocaleLowerCase().includes('select all')){
			d.click();
			
		}
	});		

}
selectAllPhotosClick();
var timInterval = setInterval( () => {
	var totalScrollHeight = $viewEl.scrollHeight;
	var currentScrollTop = $viewEl.scrollTop;
	if( currentScrollTop < totalScrollHeight ){
		$viewEl.scrollTop += 500;
		selectAllPhotosClick();
	}else{
		if( timInterval ){
			clearInterval( timInterval );
		}
	}
}, 2000);

```
