Site: https://tihloh.github.io/codescanner/

<h2>How to use?</h2><br>
javascript:
<pre>
  window.location.href = 'https://tihloh.github.io/codescanner?url=' + encodeURIComponent(window.location.href);
</pre>
<br>
It will automatically activates the scanner and will return back to referrence page with result as GET args "qrvalue" on scan success or returns without result on cancel.<br><br>
Something like:
<pre>
  http://localhost/page.html?qrvalue=123
</pre>
<br>
just add a processor for the arg "qrvalue".
<br>
<h3>Example</h3>
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
<br>
