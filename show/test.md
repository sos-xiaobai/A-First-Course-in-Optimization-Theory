# 第一次测试

## **第一段落**  
这是第一段的内容  
## ***第二段落***
这是第二段的内容  
## **第三段内容** 

>这是一个引用块，**你好**,*你好*
> - 要点1
> - 要点2  
> 
> 这是嵌套引用  
>>嵌套1  
>>嵌套2  s
>
>end

- # 1
  - ## 1.1
    段落正文......
  - ## 1.2
    段落正文......

## 代码块测试
    #include "list_cycle.h"
    #include <iostream>
    using namespace std;

    int main() {
        int num = 0;
        int input[50] = { 0 };
        int i = 0;
        cin >> num;
        do
        {
            cin >> input[i++];
        } while (getchar()!='\n');
        cin >> input[i++];
        bubbleSort(input, i);
        for (int j = 0; j < i; j++) {
            cout << input[j]<<",";
        }
        cout << endl;
        return 0;
    }

## 图床测试 
![](https://github.com/sos-xiaobai/A-First-Course-in-Optimization-Theory/blob/main/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202023-12-13%20081920.jpg?raw=true "测试悬浮显示功能")

>## 链接测试
>>### 更多详情请跳转到我的仓库 ^_^
>><https://github.com/sos-xiaobai/A-First-Course-in-Optimization-Theory>  
>>### 更多玩法前往 **[MarkDown官方教程](https://markdown.com.cn/basic-syntax/)** 学习 ^_^
>>[sos_xiaobai][1]
>
>end




[1]:https://github.com/sos-xiaobai/A-First-Course-in-Optimization-Theory
