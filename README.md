
# Illustration of wkhtmltopdf issue with google-traceur

Config :
- wkhtmltopdf 0.12.2.1 (with patched qt) on 
- Macos 10.10.2

## How to reproduce the issue ?

- git clone
- cd wkhtmltopdf-issue-traceur
- (using node) http-server in root folder
- Go to http://127.0.0.1:8080/ and make sure you see `Static message` and `Hello, world!`
- Run in root folder of the project : `wkhtmltopdf --javascript-delay 2000 --debug-javascript http://127.0.0.1:8080/ resultko.pdf`

## Result observed

The `Hello, world!` message does not show and logs show this :

```
Loading pages (1/6)
Warning: undefined:0 TypeError: 'undefined' is not a function     
Warning: undefined:0 ReferenceError: Can't find variable: traceur
Counting pages (2/6)                                               
Resolving links (4/6)                                                       
Loading headers and footers (5/6)                                           
Printing pages (6/6)
Done    
```

## Tested with 0.13 and it's ok

Tested on Windows 7 with this build http://downloads.sourceforge.net/wkhtmltopdf/wkhtmltox-0.13.0-alpha-7b36694_msvc2013-win64.exe and javscript works properly. Hower in my real case I got CSS and other issues probably due to the alpha version of the 0.13 branch.

Here is the output for 0.13 :

```
> "C:\Program Files\wkhtmltopdf\bin\wkhtmltopdf.exe" --debug-javascript  http://localhost:8080/ resultok.pdf
Loading page (1/2)
Printing pages (2/2)
Done
```





