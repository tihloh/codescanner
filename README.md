Site: https://tihloh.github.io/qrcode/

<h2>How to use?</h2>h2><br>
javascript:
<pre>
  window.location.href = 'https://tihloh.github.io/qrcode?url=' + encodeURIComponent(window.location.href);
</pre>
<br><br>
It will return back to referrence page with result as GET args "qrvalue" after success or without result on cancel.<br>
Something like:
<pre>
  http://localhost/page.html?qrvalue=123
</pre>
