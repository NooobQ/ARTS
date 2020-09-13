## ARTS Week2

### Algorithm

[Leetcode39. 组合总和]: https://leetcode-cn.com/problems/combination-sum/

没什么好说的点，DFS+回溯硬吃，注意临界条件和重复可能，重点是回溯中的溯。

```c++
//Leetcode-39-combination_sum
//search & backtrace
//just dfs & backtrace (many parameter ver 1.0)
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> ans;
        vector<int> List;
        dfs(List, candidates, ans, 0, target, 0);
        return ans;
    }
    void dfs(vector<int> &List, vector<int> &candidates, vector<vector<int>> &ans, int index, int &target, int tmp){
        
        if(tmp>=target){
            if(tmp==target){
                //for(auto foo:List)
                //    cout<<foo<<'\t';
                //cout<<'\n';
                ans.push_back(List);
            }
            return;
        }

        for(int i=index;i<candidates.size();i++){
            List.push_back(candidates[i]);
            dfs(List, candidates, ans, i, target, tmp + candidates[i]);
            List.pop_back();
        }
    }
};
```

### Review

https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/

### Technique/Tips

1. 在Linux下使用CTRL+R对历史命令进行检索（十分好用强烈推荐，不要再用上下方向键了）

2. Spring Data JPA 提供了自定义Repository的选择，可以通过定义方法名来实现较复杂的CRUD方法接口

3. IDEA中使用CTRL+Q快速查看javadoc，CTRL+SPACE补全代码，ALT+Ins生成某个类的Getter等基本函数（更实用的是使用lombok注解）

### Share

https://coolshell.cn/articles/19464.html《如何超过大多数人》

来自一位我非常喜欢的博主陈皓，他的《程序员练级攻略》给我影响非常大，十分推荐（实际上ARTS也是他所推广）。