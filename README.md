Introduction
----
**CodeScanner** provides a JavaScript-based **QR code and barcode scanner** that can be easily integrated into any **HTML-based** webpage. It supports scanning using the camera on both HTTPS and localhost environments, while also working on HTTP (though HTTP does not support camera access due to security reasons).

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
#### [HTML and JavaScript Demo](https://tihloh.github.io/codescanner/demo1.html)

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
#### Example #3:
With "pcode" param to compare the code if the same as the previous scan, if the code is different, saves to database, then loads the scanner again for the next code. 
````php
<?php	
    if (isset($_REQUEST['result'])){
        $result=$_REQUEST['result'];
        $pcode=@$_REQUEST['pcode'];
        if($pcode!=$qrvalue){
            $q="UPDATE tblemps SET scancode='$result' WHERE id='$user_id'";
            if (!$mysqli->query($q)) {
                $error = $mysqli->error;	
            }
        }
        $url = (empty($_SERVER['HTTPS']) ? 'http' : 'https') . '://$_SERVER[HTTP_HOST]/budget/dashboard?pcode=$result';
?>
        <script>window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent("<?=$url;?>");</script>
<?php
        exit;
    }
?>
<button onclick="openScanner()">Open Scanner</button>
<script>
    function openScanner(){
        window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent(window.location.href);
    }
</script>
````

Embedded Mode:
----
#### Example: Embedded Scanner on iFrame
````html
<h1>Embedded QR-Code/Barcode Scanner</h1>
<iframe src="https://tihloh.github.io/codescanner?iframe=1" id="myIframe" width="100%" height="300vp" style="-webkit-transform:scale(1);-moz-transform-scale(1);border:none;"></iframe>
<h3 id="result">Waiting...</h3>
<script>
    	function handleMessage(event) {
    	    	document.getElementById('result').innerText = event.data.message;
    	}
    	window.addEventListener('message', handleMessage);
</script>
````
#### [Embedded QR-Code/Barcode Scanner Demo](https://tihloh.github.io/codescanner/demo2.html)

Credits:
----
This project uses 
* [jsQR](https://github.com/serratus/quaggaJS) by ***cuzmo*** `Cosmo Wolfe`
* [quaggaJS](https://github.com/serratus/quaggaJS) by ***serratus*** `Christoph Oberhofer`

License:
----
CodeScanner is shared under the [MIT license](https://raw.githubusercontent.com/tihloh/codescanner/main/LICENSE). This means you can modify and use it however you want, even for comercial use. But please give this the Github repo a :star:.

