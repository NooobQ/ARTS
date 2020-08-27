## ARTS Week1

### Algorithm

[Leetcode74.搜索二维矩阵]: https://leetcode-cn.com/problems/search-a-2d-matrix/

```c++
//74.Search-a-2d-matrix
//tag:binary_search
//edge_condition attention:lowest number and highest number
//bug point:lowest number ,and trying to access the value of end iterator
//两次二分查找，第一次二分得到的数（纵向）需要处理。
//边界条件处理：比数组内最小的数还小，最大的数还大的数，每个matrix向量的开头元素与结尾元素
//只测试了大的数没测试小的数导致vector访问越界
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        
        if(matrix.empty()||matrix[0].empty())
            return false;
        int n=matrix.size();
        int m=matrix[0].size();
        int l=0,r=n;
        while(l<r){//binary_search
            int mid=(l+r)/2;
            if(matrix[mid][0]>target)
                r=mid;
            else
                l=mid+1;
        }
        
        //cout<<"test:l=\t"<<l<<endl;    
        if(l!=n&&matrix[l][0]==target)
            return true;
        if(l>0)
            l--;

        auto p=lower_bound(matrix[l].begin(),matrix[l].end(),target);
        //cout<<"test:p=\t"<<*p<<endl;
        if(p!=matrix[l].end())
            return *p==target;
        else
            return false;
    }
};
```

### Review



### Technique Tip



### Share