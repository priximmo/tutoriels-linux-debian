%title: LINUX
%author: xavki


# LINUX : Redirections & Pipe & tee


<br>

* Rediriger les flux (cf vidéo précédente stdin/stderr/stdout)
		* interaction avec le terminal	




```
>
>>
<
1>
2>
2>&1
2> 1> < 
```

```
ls nothing * 2>&1 > output.txt
echo "hello world" |& cat
```
