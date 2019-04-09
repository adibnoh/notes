# JQuery

## Ajax GET

```javascript

$.ajax({
    url: '/backend-path',
    type: 'GET',
    headers: {
        // 'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content'), // only for Laravel application
    	'Accept': 'application/json',
    },
    success:function(data){
		alert('request success');
		console.log(data); // show data from server
	},
	error: function(data){
		alert('request failed');
		console.error(data);
	}
});

```

## Ajax POST

```javascript

$.ajax({
    url: '/backend-path',
    type: 'POST',
    data: {
    	foo: 'bar'
    },
    headers: {
        // 'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content'), // only for Laravel application
    	'Accept': 'application/json',
    },
    success:function(data){
		alert('request success');
		console.log(data); // show data from server
	},
	error: function(xhr, ajaxOptions, thrownError){
		alert('request failed');
		console.error(xhr);
	}
});

```

## Ajax Upload File

```javascript

let formData = new FormData();
formData.append('file', file);
formData.append('foo', 'bar'); // you may append any additional parameter

$.ajax({
	// Your server script to process the upload
	url: '/backend-path',
	type: 'POST',

	// Form data
	data: formData,

	// Tell jQuery not to process data or worry about content-type
	// You *must* include these options!
	cache: false,
	contentType: false,
	processData: false,

	headers: {
		// 'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content'), // only for Laravel application
		'Accept': 'application/json',
	},

	// Custom XMLHttpRequest
	xhr: function() {
		var myXhr = $.ajaxSettings.xhr();
		if (myXhr.upload) {
			// For handling the progress of the upload
			myXhr.upload.addEventListener('progress', function(e) {
				if (e.lengthComputable) {
					console.log('progress value: ' + e.loaded);
					console.log('progress max: ' + e.total);
					let progressPercentage = (e.loaded/e.total)*100; // calculate percentage

				}
			} , false);
		}
		return myXhr;
	},
	success:function(data){
		alert('upload success');
		console.log(data); // show data from server
	},
	error: function(xhr, ajaxOptions, thrownError){
		alert('upload failed');
		console.error(xhr);
	}
});

```