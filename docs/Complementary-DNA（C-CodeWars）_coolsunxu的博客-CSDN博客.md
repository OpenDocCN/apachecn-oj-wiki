<!--yml
category: codewars
date: 2022-08-13 11:50:36
-->

# Complementary DNA（C CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105701911?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-105701911.nonecase](https://blog.csdn.net/coolsunxu/article/details/105701911?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-105701911.nonecase)

解题思路：

（1）遍历，对应修改

```
char *dna_strand(const char *dna) {
	char *str = calloc(strlen(dna)+1,sizeof(char));
	int count = 0;
	while(*dna!='\0') {
	    switch(*dna) {
		case 'A':
		    str[count++]='T';dna++;break;
		case 'T':
		    str[count++]='A';dna++;break;
		case 'C':
		    str[count++]='G';dna++;break;
		case 'G':
		    str[count++]='C';dna++;break;
	        default:break;
	    }
        }
        str[count] = '\0';
    return str;
}
```