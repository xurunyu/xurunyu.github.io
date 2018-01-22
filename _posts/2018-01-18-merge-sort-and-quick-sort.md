---
title: 排序
---
## 归并排序与快速排序

### 归并排序
归并排序是一种典型的分治法思想的具体实现，也是一种时间复杂度很优秀的排序算法。
归并排序分为两个步骤：

- 分

将数组按照数量平分，两个子数数量相等或者数量差1（总数为奇数）
- 合


1. 两个子数组，分别取第一个，将较小的那个保存到新的数组中
2. 重复上一步骤，直到取完某一个子数组的所有值
3. 将剩下的一个子数组的所有值加到新数组之后

递归的分解数组直到长度为1，再归并成完整的数组

python实现如下：
~~~
def merge(left,right):
    i,j = 0,0
    result = []
    while i<len(left) and j<len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i+=1
        else:
            result.append(right[j])
            j+=1
    result += left[i:]
    result += right[j:]
    return result

def mergesort(list):
    if len(list)<=1:
        return list
    mid = len(list)//2
    print(mid)
    left = mergesort(list[:mid])
    right = mergesort(list[mid:])
    return merge(left,right)
~~~


## 快速排序
快速排序也是一种分治法的具体实现。他与归并排序的区别在于分数组的方式不同。相较于归并排序，快速排序的分数组方式比较复杂，而合并方法比较简单。

- 分

取一个值Q（通常是第一个值），将数组分为两个部分：第一部分数组A，数组内所有值小于这个值；第二个部分数组B，数组内所有值大于这个值

具体实现如下:
>1）设置两个变量i、j，排序开始的时候：i=0，j=N-1；

>2）以第一个数组元素作为关键数据，赋值给key，即key=A[0]；

>3）从j开始向前搜索，即由后开始向前搜索(j--)，找到第一个小于key的值A[j]，将A[j]和A[i]互换；

>4）从i开始向后搜索，即由前开始向后搜索(i++)，找到第一个大于key的A[i]，将A[i]和A[j]互换；

>5）重复第3、4步，直到i=j； (3,4步中，没找到符合条件的值，即3中A[j]不小于key,4中A[i]不大于key的时候改变j、i的值，使得j=j-1，i=i+1，直至找到为止。找到符合条件的值，进行交换的时候i， j指针位置不变。另外，i==j这一过程一定正好是i+或j-完成的时候，此时令循环结束）。

- 合

按照  数组A 值Q 数组B 进行合并

python实现如下：
~~~
def quicksort(list,left,right):
    if left>=right:
        return list
    key = list[left]
    #先保存起止两点
    low = left
    high = right

    while left<right:
        #将列表从后往前与KEY值进行比较，直到找到比KEY值小的数字
        while left<right and list[right] >= key:
            right-=1
        list[left] = list[right]
        print(list)
        #同样将列表从前往后与KEY直比较，直到找到比KEY值大的数字
        while left<right and list[left] <= key:
            left+=1
        list[right] = list[left]
    #循环以上过程直到left right两指针相等，将key值赋值给指针位置
    list[right] = key

    quicksort(list,low, left-1)
    quicksort(list,right+1,high)
    return list
~~~
