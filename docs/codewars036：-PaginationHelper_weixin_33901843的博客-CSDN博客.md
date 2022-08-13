<!--yml
category: codewars
date: 2022-08-13 11:44:11
-->

# codewars036: PaginationHelper_weixin_33901843的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33901843/article/details/92001774?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-92001774.nonecase](https://blog.csdn.net/weixin_33901843/article/details/92001774?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-92001774.nonecase)

5 kyu [Source](https://www.codewars.com/kata/515bb423de843ea99400000a/train/java)

```
//https://www.codewars.com/kata/515bb423de843ea99400000a/train/java
package codewars.dec;
import java.util.Arrays;
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;

public class PaginationHelperTest{
    private PaginationHelper<Character> helper = new PaginationHelper(Arrays.asList('a','b','c','d','e','f'),4);
    @Test
    public void testSomething(){
        assertEquals(2, helper.pageCount());
        assertEquals(6, helper.itemCount());
        assertEquals(4, helper.pageItemCount(0));
        assertEquals(2, helper.pageItemCount(1));
        assertEquals(-1, helper.pageItemCount(2));
        assertEquals(1, helper.pageIndex(5));
        assertEquals(0, helper.pageIndex(2));
        assertEquals(-1, helper.pageIndex(20));
        assertEquals(-1, helper.pageIndex(-10));               
    }
} 
```

```
package codewars.dec;
import java.util.List;
public class PaginationHelper<I> {
    private List<I> collection;
    private int itemsPerPage;
    public PaginationHelper(List<I> collection, int itemsPerPage){
        this.collection = collection;
        this.itemsPerPage = itemsPerPage;
    }    
    public int itemCount(){
        return collection.size();
    }    
    public int pageCount(){
       int count = itemCount() % itemsPerPage == 0 ? itemCount() / itemsPerPage : itemCount() / itemsPerPage + 1;
        return count;
    }    
    public int pageItemCount(int pageIndex){
        if(pageIndex >= pageCount()){
            return -1;
        }            
        int count = pageIndex < pageCount() - 1 ? itemsPerPage : itemCount() - itemsPerPage * (pageCount() - 1);
        return count;
    }        
    public int pageIndex(int itemIndex){
        int pageIndex = -1;
        if(itemIndex >= itemCount() || itemIndex < 0){
            return pageIndex;
        }    
        pageIndex = itemIndex / itemsPerPage;
        return pageIndex;
    }    
} 
```