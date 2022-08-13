<!--yml
category: codewars
date: 2022-08-13 11:39:51
-->

# Codewars - Regular Expression for Binary Numbers Divisible by n_wynist的博客-CSDN博客

> 来源：[https://blog.csdn.net/u012345506/article/details/104578534?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-104578534-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/u012345506/article/details/104578534?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-104578534-null-null.142^v40^control,185^v2^control&utm_term=codewars)

考虑按照模 n n n求出DFA，然后将DFA转换成正则表达式。
如果用dp来做的话，产生的正则表达式长度是 O ( 4 n ) O(4^n) O(4n)的，建议用删点来做，虽然长度的界似乎差不多，但还是比dp的来的短。
尽量处理一下生成的表达式中冗余的部分，然后每次删点时随机一下就ok了。

```
function regexDivisibleBy(n) {
	var i,j,i,d,t,mt=[],dp=[],iz=[],oz=[];for(i=0;i<n;++i)for(j=0,mt.push([]);j<n;++j)mt[i].push(-1);
	for(i=0;i<n;++i)iz.push(0),oz.push(0);
	for(i=0;i<n;++i)for(j=0;j<2;++j)mt[i][(i*2+j)%n]=j;
	for(i=0;i<n;++i)for(dp.push([]),j=0;j<n;++j)dp[i].push('');
	for(i=0;i<n;++i)for(j=0;j<n;++j)if(mt[i][j]>=0)
	    dp[i][j]=i==j?`${mt[i][j]}*`:`${mt[i][j]}`,iz[j]++,oz[i]++;
	var ck=e=>{
	    var x=0,i;for(i=0;i<e.length;++i){
	        if(e[i]=='(')--x;if(e[i]==')')++x;if(e[i]=='|'&&!x)return 0;
	    }
	    return 1;
	}
	var p,bd=[],sp=[],rt=[],root=Math.ceil(Math.random())%6+1;
	for(i=0;i<n;++i)bd[i]=1;for(i=1;i<n;++i)sp.push(i);
	for(i=1;i<n;++i)rt[i]=Math.random();sp.sort((a,b)=>rt[a]-rt[b]);
	for(p=0;p<n-1;++p){
	    bd[i=sp[p]]=0,t=dp[i][i].length?`(${dp[i][i]})*`:``;
	    if(dp[i][i].length==1)t=`${dp[i][i]}*`;
	    else if(dp[i][i]=='1*'||dp[i][i]=='0*')t=dp[i][i];
	    for(j=0;j<n;++j)if(bd[j]&&dp[i][j].length){
	        for(k=0;k<n;++k)if(bd[k]&&dp[k][i].length){
	            var a=dp[k][j].length==1?dp[k][j]:`(${dp[k][j]})`;
	            var b=ck(dp[k][i])?dp[k][i]:`(${dp[k][i]})`;
	            var c=ck(dp[i][j])?dp[i][j]:`(${dp[i][j]})`;
	            dp[k][j]=dp[k][j].length?`${a}|(${b}${t}${c})`:`${b}${t}${c}`;
	        }
	    }
	}
	return n==1?`1`:`^(${dp[0][0]})+$`;
} 
```

这个网站还是挺好玩的。