![](Pictures/二分查找.jpg)  
[[二分查找为什么总是写错？_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1d54y1q7k7/?spm_id_from=333.337.search-card.all.click&vd_source=30d3e14399ca7c5e889670a30af532e1)]  

*题目：第1行为正整数n和整数x，第2行为n个整数，n ≤ 1000。
         x在n个整数中出现的位置下标。*  
```
样例输入：5 13 
         1 2 13 24 55
         
样例输出：2
```  
*样例代码*
```Cpp
#include <iostream>
using namespace std;
int binarySearch(int arr[], int left, int right, int m)
{
    int mid;
    while (left + 1 != right)
    {
        mid = (left + right) / 2;
        if (arr[mid] == m)
        {
            return mid;
        }
        else if (arr[mid] > m)
        {
            right = mid;
        }
        else if (arr[mid] < m)
        {
            left = mid;
        }
        else
	        return -1;
    }
}
int main()
{
    int n, m;//m为查询的数字
    cin >> n >> m;
    int arr[n] = {0};
    for (int i = 0; i < n; i++)
    {
        cin >> arr[i];
    }
    int result = binarySearch(arr, -1, n, m);
    cout << result << endl;
}
```  

