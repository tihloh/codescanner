<a href="https://tihloh.github.io/codescanner/demo2.html" target=blank_>SHOW DEMO #1</a>
<h2>How to use?</h2>
javascript:
<pre><code>
window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent(window.location.href);
</code></pre>
<br>
It will automatically activates the scanner and will return back to referrence page with result as GET param "qrvalue" on scan success or returns without result on cancel.
<br>
<br>
Something like:
<pre>
http://localhost/page.html?qrvalue=123
</pre>
<br>
just add a processor for the arg "qrvalue".
<br>
<h3>Example #1</h3>
<pre>
<code>
&lt;?php	
    if (isset($_REQUEST['qrvalue'])){
    	$qrvalue=$_REQUEST['qrvalue'];
    	echo "Scan result: ".$qrvalue;
    }
?&gt;
&lt;button onclick="openScanner()"&gt;Open Scanner&lt;/button&gt;
&lt;script&gt;
    function openScanner(){
        window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent(window.location.href);
    }
&lt;/script&gt;
</code>
</pre>
<h3>Example #2</h3>
Embedded Scanner on iFrame
<pre><code>
&lt;h1&gt;Embedded QR-Code/Barcode Scanner&lt;/h1&gt;
&lt;iframe src="https://tihloh.github.io/codescanner?iframe=1" id="myIframe" width="100%" height="300vp" style="-webkit-transform:scale(1);-moz-transform-scale(1);border:none;"&gt;&lt;/iframe&gt;
&lt;h3 id="result"&gt;Waiting...&lt;/h3&gt;
&lt;script&gt;
    	function handleMessage(event) {
    	    	document.getElementById('result').innerText = event.data.message;
    	}
    	window.addEventListener('message', handleMessage);
&lt;/script&gt;
</code></pre>
<a href="https://tihloh.github.io/codescanner/demo2.html" target=blank_>SHOW DEMO #2</a>
<hr>
<h3>Example #3</h3>
With "pcode" param to compare the code if the same as the previous scan, if the code is different, saves to database, then loads the scanner again for the next code.
<pre>
<code>
&lt;?php	
    if (isset($_REQUEST['qrvalue'])){
        $qrvalue=$_REQUEST['qrvalue'];
        $pcode=@$_REQUEST['pcode'];
        if($pcode!=$qrvalue){
            $q="UPDATE tblemps SET scancode='$qrvalue' WHERE id='$user_id'";
            if (!$mysqli-&gt;query($q)) {
                $error = $mysqli-&gt;error;	
            }
        }
        $url = (empty($_SERVER['HTTPS']) ? 'http' : 'https') . '://$_SERVER[HTTP_HOST]/budget/dashboard?pcode=$qrvalue';
?&gt;
        &lt;script&gt;window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent("&lt;?=$url;?&gt;");&lt;/script&gt;
&lt;?php
        exit;
    }
?&gt;
&lt;button onclick="openScanner()"&gt;Open Scanner&lt;/button&gt;
&lt;script&gt;
    function openScanner(){
        window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent(window.location.href);
    }
&lt;/script&gt;
</code>
</pre>
