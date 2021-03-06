﻿![在这里插入图片描述](https://img-blog.csdnimg.cn/20200414111000250.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)

冒泡排序，顾名思义就像水沸腾时，沸腾的水泡自下而上，由大到小的往水面沸腾.

从大一接触唐浩强爷爷的C语言，老师讲的第一个排序算法便是冒泡排序.  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191026223316915.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)

### 一、冒泡思想

冒泡排序是**交换排序**的一种，在基础排序算法中还有[**快速排序**](https://blog.csdn.net/weixin_43232955/article/details/89279242). 

冒泡排序（Bubble Sort）也是一种简单直观的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序有误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端，故名“冒泡排序”.

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040916381553.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)

<center>算法步骤</center>

***

1. 比较相邻的元素。如果第一个比第二个大，就交换他们两个
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。
3. 针对所有的元素重复以上的步骤，除了最后一个。
4. 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

***

<center>算法演示</center>

***

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191026233439309.gif)

<center>排序动画过程解释</center>

***

1. 将天平放在序列的右端，并比较天平左右的数字
2. 在这种情况下我们比较 3 和 8
3. 比较后如果右边的数字较小，则被交换
4. 因为 8 大于 3 ，所以数字不用交换
5. 比较完成后，将天平向左移动一个位置，比较数字
6. 因为 3 大于 2 ，所以数字不用交换
7. 比较完成后，逐一移动天平，比较数字
8. 此时 2 小于 4 ，所以左右的数字互相交换
9. 重复同样的操作，直到天平移动到左端
10. 。。。。。。
11. 天平到达左端
12. 经过上述的操作，数列中最小的数字已经移动到左端
13. 将天平返回右端
14. 重复相同的操作，直到所有数字都被排序

> 以上动画演示及详细解释来源于微型公众号【[**五分钟学算法**](https://mp.weixin.qq.com/s/HDbW5_On8gEjygrlIfPlIQ)】，很多基础的排序算法和数据结构动图解释的很清楚，推荐一波

### 二、冒泡实现及优化

通过以上的讲解，相信大家对冒泡排序的思维有一定的了解。 我们通过一个简单的例子，用代码来实现
我们通过这8个数从小到大来排序：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191027221659943.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191026231040483.gif)

> [【**数据结构和算法动态可视化网站**】](https://visualgo.net/zh)，动图演示很形象具体

***

**代码使用双层循环进行排序**

- 外部循环控制每轮排序元素的个数，即参与冒泡的元素个数
- 内部循环实现每一轮的冒泡处理，即每轮的排序趟数。先进行元素比较，再进行元素交换

排序过程详解：

- **n个元素，进行`n - 1`轮排序**

- **每轮排序的趟数为参与此轮排序的元素个数**
  ![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pcXFjb2RlLWJsb2cub3NzLWNuLWJlaWppbmcuYWxpeXVuY3MuY29tL2ltZy8yMDIwMDcxMTEwMTE1NS5wbmc?x-oss-process=image/format,png)
  
  #### 1. 基础版本
  
  ```java
   /**
     * @自下往上冒泡
     * 由小到大排序
     * @param arr
     */
    public static void bubbleSort_toLarge(int[] arr) {
        int len = arr.length - 1;
        //待排序元素个数 n - 1, 剩下最后一个元素默认有序了
        for (int i = len; i > 0; i--) {
            //每轮排序趟数
            for (int j = 0; j < i; j++) {
                if(arr[j] > arr[j+1] ) {
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }
  ```
  
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191027133345409.png)
  自下往上冒泡-----由大到小排列
  
  ```java
   /**
     * @自上往下冒泡
     * 由大到小排序
     * @param arr
     */
    public static void bubbleSort_toSmall(int[] arr) {
        int len = arr.length - 1;
        for (int i = 0; i < len; i++) {
            for (int j = 0; j < len - i; j++) {
                if(arr[j] < arr[j+1] ) {
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }
  ```
  
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200409160253453.png)
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191027224841457.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)
  
  #### 2. 升级版本
  
  那碰到这样的数列，或者直接就是有序的数列，那排序的效率岂不是很低？
  ![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pcXFjb2RlLWJsb2cub3NzLWNuLWJlaWppbmcuYWxpeXVuY3MuY29tL2ltZy8yMDIwMDcxMTA5MTk0NS5wbmc?x-oss-process=image/format,png)
  我只需要一轮冒泡就完成了排序，但是依然得全走一遍

与基础版本相比较，升级版本利用`flag`作为标记。

在内层每一轮的排序中，如果有元素发生了交换，则`flag = true`，说明数列无序；

如果元素有序，此时**flag**为false，`!flag`为 true，证明此时数列已经有序了，则冒泡排序结束

```java
public static int[] bubble(int[] arr) {
    int len = arr.length;
    //待排序元素个数 n - 1
    for (int i = len - 1; i > 0; i--) {
        //重置flag,进行本次判断，默认此轮排序无序
        boolean flag = false;
        for (int j = 0; j < i; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                flag = true;
            }
        }
        //此趟排序没有进行数值交换,flag = false
        if (!flag)
            break;
    }
    return arr;
}
```

`break`跳出的是外层循环，即满足条件，则排序结束！
![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pcXFjb2RlLWJsb2cub3NzLWNuLWJlaWppbmcuYWxpeXVuY3MuY29tL2ltZy8yMDIwMDcxMTA5MjUwMS5wbmc?x-oss-process=image/format,png)

- 第一轮循环将6沉底后，开始第二轮循环
- 在第二轮循环中，由于元素有序，不进入到`for(int j = 0; j < i; j++)`，所以`flag = false`
- 此时，直接**break**出外层`for(int i = len-1; i > 0; i--)`循环。因为冒泡是逐个比较的，发现在第二轮的循环中，两两比较均符合有序，==说明整个数列此时已经有序了==
- break跳出外层循环，结束排序即可
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029225056410.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)
  我们再换一个新的数列，它的前半部分无序（3，4，2，1），后半部分有序（5，6，7，8），并且后半部分的最小值也大于前半部分的最大值，就是只用排前半部分就好了，直接把它放到后半部前面就好。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029225005353.png)
此时，还用**版本2**的升级版也做了一半的无用功，还有待需要继续优化

挤牙膏，高极版的来了...

***

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200602000352108.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)
每次排序前或排序后数组的后面都有一部分已经有序，这时我们只要记下最后一次排序的数组的下标，下次排序的时候就可以只排序到此下标位置即可，因为后面的已经有序了。

#### 3. 高级版

```java
/**
 * @Author: Mr.Q
 * @Date: 2020-04-09 16:12
 * @Description:标志位该进版，针对一半有序一半无序
 * { 3, 4, 2, 1, 5, 6, 7, 8 }
 */
public static int[] bubble(int[] arr) {
    for (int i = arr.length - 1; i > 0; i--) {
        //初始化border，让 border - 1 <= 0 即可
        int border = 1;
        for (int j = 0; j < i; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                //3  4  2  1  5[border]  6  7  8 待排序元素个数为(j+1)个
                border = j + 1;
            }
        }
        //更新待排序元素的边界,下一次比较到记录位置即可
        i = border;
    }
    return arr;
}
```

因为此时后半段数列有序，当把元素4放到5之前时，`border = 3`，后面便不再比较

这样，相对于上一个版本，针对这种半有序，半无序的数列效率又有提高了不少呢！

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029233551914.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)
这次，我要排这个呢？好像上面的效率又不行了...
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031215214901.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)
上面的 **版本3--高级版** 其实就可以了，但是，针对此还有一中特定的排序算法（谁发明的，此时我要膜拜三分钟）

#### 4. 鸡尾酒排序

[**鸡尾酒排序**](https://baike.sogou.com/v58239106.htm?fromTitle=%E9%B8%A1%E5%B0%BE%E9%85%92%E6%8E%92%E5%BA%8F)
<img src = "https://img-blog.csdnimg.cn/20191029234556339.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70" width = "60%">

冒泡排序的每一轮都是**从左到右来比较元素，是单向的位置交换**；

但是，鸡尾酒排序元素比较和交换是**双向的**

排序过程如下：

**第1趟：**

和基础冒泡排序一样，从左到右走一趟，把8沉底

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031215833315.png)
**第2趟：**

从右往左冒泡（从倒数第二位开始）

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019103122055667.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031221113100.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIzMjk1NQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031221155536.png)
**第3趟：**

继续从左向右走（虽然有序，但继续判断，类似于最基础的冒泡）

**第4趟：**

从右往左（从倒数第三位开始）

**直到没有元素再发生交换而结束**

```java
public static int[] cocktailSort(int[] arr) {
    for (int i = 0; i < arr.length / 2; i++) {
        boolean flag = false;
        //奇数轮,从左向右比较交换
        for (int j = 0; j < arr.length - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                //此趟排序没有进行数值交换
                flag = true;
            }
        }
        //在一趟排序中没有发生过交换
        if (!flag)
            break;
        //偶数轮,从右向左比较交换
        for (int j = arr.length - 1; j > i; j--) {
            if (arr[j] < arr[j - 1]) {
                int temp = arr[j];
                arr[j] = arr[j - 1];
                arr[j - 1] = temp;
                //此趟排序没有进行数值交换
                flag = true;
            }
        }
        //在一趟排序中没有发生过交换
        if (!flag)
            break;
    }
    return arr;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019103122164067.png)
**鸡尾酒排序与冒泡排序不同的地方**

鸡尾酒排序等于是冒泡排序的轻微变形。不同的地方在于从低到高然后从高到低，而冒泡排序则仅从低到高去比较序列里的每个元素。他可以得到比冒泡排序稍微好一点的性能，原因是冒泡排序只从一个方向进行比对（由低到高），每次循环只移动一个项目。但是，鸡尾酒排序元素比较和交换是**双向的**。

---------------------------------------------

**《被排序算法吊打系列汇总》**

- [**被排序算法吊打之—冒泡排序 你需要了解的三种优化**](https://blog.csdn.net/weixin_43232955/article/details/102761799)

- [**被排序算法吊打之—选择排序**](https://blog.csdn.net/weixin_43232955/article/details/105521656)

- [**被排序算法吊打之—插入排序**](https://blog.csdn.net/weixin_43232955/article/details/105577372)

- [**被排序算法吊打之—希尔排序**](https://blog.csdn.net/weixin_43232955/article/details/105605403)

- [**被排序算法吊打之—归并排序**](https://blog.csdn.net/weixin_43232955/article/details/105610703)

- [**被排序算法吊打之—快速排序**](https://blog.csdn.net/weixin_43232955/article/details/89279242)

- [**被排序算法吊打之—堆排序**](https://blog.csdn.net/weixin_43232955/article/details/105824871)

----------------------

【参考文章】

1. [图解数据结构](https://mp.weixin.qq.com/s/HDbW5_On8gEjygrlIfPlIQ)
2. [《漫画算法》](https://item.jd.com/12513751.html)
