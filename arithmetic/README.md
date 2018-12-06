## 算法小练

### 选择排序

```java
/**每日一练 2018/12/05
 * 选择排序: 每次选择一个数 然后遍历其后的每一个数,和这个数比较
 * 时间复杂度:O(N^2)
 * 算法特点: 排序时间和初始顺序无关 无论顺序如何都是O(N^2)
 * */
private void sortIntegers(int[] arr){
    if(arr == null || arr.length <= 1){ return; }
    for ( int i =0;i < arr.length ;i++){
        int min = i;
        for (int j = i +1;j<arr.length;j++){
            if(arr[j] < arr[min]){
                min = j;
            }
        }
        int tmp = arr[min];
        arr[min] = arr[i];
        arr[i] = tmp;
    }
}
```

### 插入排序

```java
/**每日一练 2018/12/06
 * 插入排序:像打牌时整理牌,小的插入到左边,大的插入到右边
 * 算法特点: 最坏的情况下复杂度O(N^2)
 * 依赖于初始排序顺序 ,特别适合于部分有序数组 完全是有序数组的情况下 复杂度为O(N)
 * 逆时排序是复杂度为 O(N^2)
 * */
private void sortIntegers2(int[] arr){
    if(arr == null || arr.length <= 1){ return; }
    for(int i=1;i<arr.length ;i++){
        for(int j =i;j>0;j++){
            if(arr[j] <arr[j-1]){
                int tmp = arr[j];
                arr[j-1] = tmp;
            }else{
                break;
            }
        }
    }
}
```