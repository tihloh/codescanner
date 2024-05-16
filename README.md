Site: https://tihloh.github.io/qrcode/

<h2>How to use?</h2><br>
javascript:
<pre>
  window.location.href = 'https://tihloh.github.io/qrcode?url=' + encodeURIComponent(window.location.href);
</pre>
<br>
It will automatically activates the scanner and will return back to referrence page with result as GET args "qrvalue" on scan success or returns without result on cancel.<br><br>
Something like:
<pre>
  http://localhost/page.html?qrvalue=123
</pre>
<br><br>
just add a processor for the arg "qrvalue".
<br><br>
<h3>Example</h3><br>
<code>
  <?php	
    if (isset($_REQUEST['qrvalue'])){
      $qrvalue=$_REQUEST['qrvalue'];
      echo "Scan result: ".$qrvalue;
    }
  ?>
  <button onclick="openScanner()">Open Scanner</button>
  <script>
    function openScanner(){
      window.location.href = 'https://tihloh.github.io/qrcode?url=' + encodeURIComponent(window.location.href);
    }
  </script>
</code><br><br>
<a href="https://tihloh.github.io/qrcode/tryme.html">Try Me</a>
