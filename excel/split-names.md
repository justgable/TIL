# Spliting Names

Periodically I have to clean up a list of names that have the first and last
names in one cell.

## Get string AFTER last space

```
=TRIM(RIGHT(SUBSTITUTE(A1," ",REPT(" ",LEN(A1))),LEN(A1)))
```

## Get string BEFORE last space

```
=LEFT(A1,SEARCH("^^",SUBSTITUTE(A1," ","^^",LEN(A1)-LEN(SUBSTITUTE(A1," ",""))))-1)
```

[Source](https://www.mrexcel.com/forum/excel-questions/498759-find-text-after-last-space-string-post2462337.html#post2462337)
[Source](https://www.excelforum.com/excel-general/941094-extract-all-text-before-final-space-in-cell.html#post3332913)
