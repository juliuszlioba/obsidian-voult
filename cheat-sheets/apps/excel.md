convert "5,95" to "5.95 EUR":

```excel
=SUBSTITUTE(F2;",";".")&" EUR"
```

match D2 from H2:H5 list

```excel
=IF(ISNUMBER(MATCH( D2 ; $H$2:$H$5 ; 0 ));"match";"no match")
```