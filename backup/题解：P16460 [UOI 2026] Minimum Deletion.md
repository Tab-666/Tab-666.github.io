搬运我的洛谷题解，原文创作时间：2026-05-14 19:30。

# [P16460 [UOI 2026] Minimum Deletion](https://www.luogu.com.cn/problem/P16460)
## 思路
这道题要找一个最小操作次数，使数组的最小未出现值 $m$ 的值不超过 $k$。

思路很简单，要让 $m$ 不超过 $k$，必须满足**所有小于 $m$ 的数都在数组中**。

对于每个合法的 $m$，删除次数就是 $m$ 在数组中出现的次数，最终输出所有合法的 $m$ 中出现的次数最少的那个即可。
## 代码
```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n,k;
    cin>>n>>k;
    int cnt[10]={0};
    for(int i=0;i<n;i++){
        int x;
        cin>>x;
        cnt[x]++;// 统计0至9每个数在数组出现的个数
    }
    int ans=n;
    for(int m=0;m<=k;m++){
        bool flag=true;
        // 检查每个数是否都在
        for(int i=0;i<m;i++){
            if(cnt[i]==0){
                flag=false;
                break;
            }
        }
        if(flag==true){
            if(m<10)ans=min(ans,cnt[m]);
            else ans=min(ans,0);
        }
    }
    cout<<ans;
	return 0;
}
```
时间复杂度：$O(n + k^2)$，对于 $n \le 10^3$、$k \le 10$ 的数据范围完全足够。