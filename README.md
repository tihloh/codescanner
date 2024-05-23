Introduction
----
**CodeScanner** provides a JavaScript-based **QR code and barcode scanner** that can be easily integrated into any **HTML-based** webpage. It supports scanning using the camera on both HTTPS and localhost environments, while also working on HTTP (though HTTP does not support camera access due to security reasons).

Demo
----
#### [Demo #1](https://tihloh.github.io/codescanner/demo1.html)
#### [Demo #2](https://tihloh.github.io/codescanner/demo2.html)

Features:
----
* **QR Code Scanning**: Quickly scan and decode QR codes.
* **Barcode Scanning**: Supports various barcode formats.
* **Camera Access**: Utilizes the device's camera for scanning (HTTPS and localhost only).
* **Cross-Browser Compatibility**: Works on major browsers that support camera access.
* **Two Modes**:
  * **External Mode**: Open scanner in a new window on button click.
  * **Embedded Mode**: Embed scanner within the page using an iframe with continuous multiple scanning capability.

External Mode:
----

#### Example #1: Using only html and javascript
````html
<h3 id="result">Result: </h3>
<button onclick="openScanner()">Open Scanner</button>
<script>
    function openScanner(){
        window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent(window.location.href);
    }
    window.onload = (event) => {
        const urlParams = new URLSearchParams(window.location.search);
        const result = decodeURIComponent(urlParams.get('result'));
        document.getElementById('result').innerText = "Result: " + result;
    };
</script>
````
#### [Demo #1](https://tihloh.github.io/codescanner/demo1.html)

#### Example #2: Using PHP
````php
<?php	
    if (isset($_REQUEST['result'])){
    	$result=$_REQUEST['result'];
    	echo "Scan result: ".$result;
    }
?>
<button onclick="openScanner()">Open Scanner</button>
<script>
    function openScanner(){
        window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent(window.location.href);
    }
</script>
````

##### Result:
![Result](https://s3-eu-west-1.amazonaws.com/js-barcode/barcodes/simple.svg)

License:
----
CodeScanner is shared under the [MIT license](https://raw.githubusercontent.com/tihloh/codescanner/main/LICENSE). This means you can modify and use it however you want, even for comercial use. But please give this the Github repo a :star:.

