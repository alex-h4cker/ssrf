# ssrf
ssrf reserch
SSRF or Server Side Request Forgery means fraud in server side requests. In this type of vulnerability, an attacker can connect the server to send malicious requests to internal or external resources. This vulnerability allows the attacker to access sensitive resources and may lead to leaking of sensitive information, intrusion into internal services or even control over the server.

What access does the SSRF vulnerability give the attacker

1_ Scan port
To perform port scan, it is enough to use http or https protocol
for example

    https://127.0.0.1:80

2_ Reading files
We use //:file to read files
for example

    file:///etc/passwd

blind ssrf:

For example, we want to perform a port scan on the target

Payload
  
    http://127.0.0.1:80

If the vulnerability is blind ssrf, how to find out whether the port is open or wrong

    1_ Pay attention to the content-length header
    2- Pay attention to the page loading time

Some functions accept URLs as input, which allows SSRF vulnerabilities if the user can manipulate the data

    _file_get_contents()
    fopen()
    file()
    md5_file()

Parameters that may have an SSRF vulnerability

    ?dest=
    ?redirect=
    ?uri=
    ?path=
    ?continue=
    ?url=
    ?window=
    ?next=
    ?data=
    ?reference=
    ?site=
    ?html=
    ?val=
    ?validate=
    ?domain=
    ?callback=
    ?return=
    ?page=
    ?feed=
    ?host=
    ?port=
    ?to=
    ?out=
    ?view=
    ?dir=

file uoload - ssrf

Web applications commonly utilize PDF generation libraries to generate PDF documents. These pages usually allow users to input the data and then generate a PDF document
Some of the most popular PDF generation libraries used in web applications :

    TCPDF
    PDFKit
    iText
    FPDF

Payload:

    <script>
    x=new XMLHttpRequest; 
    x.onload=function(){document.write(btoa(this.responseText))}; 
    x.open("GET","file:///etc/passwd");x.send() 
    </script>
