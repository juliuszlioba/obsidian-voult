Flatten form:
```javascript
if (app.viewerType=="Reader") {
	for (var i=0; i<this.numFields; i++) {
		var f = this.getField(this.getNthFieldName(i));
		if (f==null) continue;
		f.readonly = true;
	}	
} else this.flattenPages();
```
