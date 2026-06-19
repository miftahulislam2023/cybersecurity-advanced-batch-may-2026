# Class 8

## Commands
```bash
miftah@miftahcoding:~$ echo "I am"
I am
miftah@miftahcoding:~$ echo "I am" > t1
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   asdsa   m.txt   mifta   o.txt   output.txt   snap   t1
miftah@miftahcoding:~$ rm asdsa m.txt o.txt output.txt 
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   mifta   snap   t1
miftah@miftahcoding:~$ rm -rf mifta/
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   snap   t1
miftah@miftahcoding:~$ cat t1
I am
miftah@miftahcoding:~$ echo "Miftahul " > t2
miftah@miftahcoding:~$ echo "Islam." > t3
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   snap   t1   t2   t3
miftah@miftahcoding:~$ cat t1 t2 t3
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ cat t?
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ echo "asda" > asd?.asd*
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos  'asd?.asd*'   snap   t1   t2   t3
miftah@miftahcoding:~$ cat asd\?.asd\* 
asda
miftah@miftahcoding:~$ rm asd\?.asd\* 
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   snap   t1   t2   t3
miftah@miftahcoding:~$ cat t*
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ cat t* >> output
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   output   snap   t1   t2   t3
miftah@miftahcoding:~$ cat output 
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ cat t* > output
miftah@miftahcoding:~$ cat output 
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ c

miftah@miftahcoding:~$ echo "asdas" >> m
miftah@miftahcoding:~$ echo "asdas" > m
miftah@miftahcoding:~$ cat m
asdas
miftah@miftahcoding:~$ echo "asdas" >> m
miftah@miftahcoding:~$ echo "asdas" >> m
miftah@miftahcoding:~$ echo "asdas" >> m
miftah@miftahcoding:~$ cat m
asdas
asdas
asdas
asdas
miftah@miftahcoding:~$ echo "asdas" > m
miftah@miftahcoding:~$ cat m
asdas
miftah@miftahcoding:~$ echo "asdas" >> m
miftah@miftahcoding:~$ echo "asdas" >> m
miftah@miftahcoding:~$ echo "asdas" >> m
miftah@miftahcoding:~$ cat m
asdas
asdas
asdas
asdas
miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   m   output   snap   t1   t2   t3
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat m
asdas
asdas
asdas
asdas
I am
Miftahul 
Islam.
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ cat t* > m
miftah@miftahcoding:~$ cat m
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ 
```

## Concatenation
```bash

miftah@miftahcoding:~$ ls
 Desktop   Documents   Downloads   'Miftahul Islam'   Music   Pictures   Public   Templates   Videos   m   output   snap   t1   t2   t3
miftah@miftahcoding:~$ cat m
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ cat m >> m
cat: m: input file is output file
miftah@miftahcoding:~$ cat m
I am
Miftahul 
Islam.
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat t* >> m
miftah@miftahcoding:~$ cat m
miftah@miftahcoding:~$ 

```

## Interactive Deletion
```bash
miftah@miftahcoding:~$ rm -i t*
rm: remove regular file 't1'? 
rm: remove regular file 't2'? 
rm: remove regular file 't3'? 
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  habijabi  snap  t1  t2  t3
miftah@miftahcoding:~$ rm -i t*
rm: remove regular file 't1'? y
rm: remove regular file 't2'? n
rm: remove regular file 't3'? 
miftah@miftahcoding:~$ ls
cybersecurity-batch-2  habijabi  snap  t2  t3
miftah@miftahcoding:~$ 
```

## Notes
- A question mark (?) can be used to indicate “any single character” within the file name. An asterisk (*) can be used to indicate “zero or more characters”. These are sometimes referred to as “wildcard” characters.
- pager, more, less -> :q

## Good naming practice

- When you consider both case sensitivity and escaping, a good rule of thumb is to keep your file names all lower case, with only `letters`, `numbers`, `underscores` and `hyphens`. For files there’s usually also a dot and a few characters on the end to indicate the type of file it is (referred to as the “file extension”). This guideline may seem restrictive, but if you end up using the command line with any frequency you’ll be glad you stuck to this pattern.