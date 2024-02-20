Remove "Save" button and flatten form:
```javascript
var saveBtn = this.getField("save_btn");
saveBtn.buttonSetCaption("", 0);
saveBtn.strokeColor = ["RGB",1,1,1];
saveBtn.fillColor = ["RGB",1,1,1];
saveBtn.textColor = ["RGB",1,1,1];

if (app.viewerType=="Reader") {
	for (var i=0; i<this.numFields; i++) {
		var f = this.getField(this.getNthFieldName(i));
		if (f==null) continue;
		f.readonly = true;
	}	
} else this.flattenPages();
```

Remove all buttons from file and flatten form:
```javascript
if (app.viewerType=="Reader") {
  for (var i=0; i<this.numFields; i++) {
    var f = this.getField(this.getNthFieldName(i));

    if(f.type=="button"){
      f.buttonSetCaption("", 0);
      f.strokeColor = ["RGB", 1, 1, 1];
      f.fillColor = ["RGB", 1, 1, 1];
      f.textColor = ["RGB", 1, 1, 1];
    };

    if (f==null) continue;
    f.readonly = true;
  }
} else {
  for (var i = 0; i < this.numFields; i++) {
    var f = this.getField(this.getNthFieldName(i));

    if (f.type == "button") {
      f.buttonSetCaption("", 0);
      f.strokeColor = ["RGB", 1, 1, 1];
      f.fillColor = ["RGB", 1, 1, 1];
      f.textColor = ["RGB", 1, 1, 1];
    }

    if (f == null) continue;
  }

  this.flattenPages();
}
```