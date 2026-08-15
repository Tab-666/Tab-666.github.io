搬运我的洛谷题解，原文创作时间：2026-05-19 19:41。

# [P16556 [ICPC 2026 LAC] Jaime' s Palace](https://www.luogu.com.cn/problem/P16556)
## 思路
一道很不错的贪心题。

有 $P$ 个盘子，每天拿 $K_i$ 个盘子，用完可以按照任何顺序放回去，要想个办法求出最大的盘子使用次数。

可以用栈模拟，因为题目里一摞碟子就很像栈结构。

从栈（题目中的一摞盘子）取出使用的盘子，把每天使用过的盘子按当前**已经使用过**的次数**从小到大**排序，然后放回栈顶。这样就可以让使用次数较少的盘子靠近栈顶，从而在接下来的天数更容易选中，可平衡盘子的使用次数。

模拟完之后，所有盘子的使用次数的最大值就是答案，直接输出即可。
## 代码
直接献上我的代码好吧。

```cpp line-numbers
#include<bits/stdc++.h>
using namespace std;
int main(){
    int P,D;
    cin>>P>>D;
    vector<int>k(D);
    for(int i=0;i<D;i++)cin>>k[i];
    vector<int>cnt(P,0);//记录每个使用次数
    vector<int>st(P);//栈，但是数组模拟，因为这样就可以随机访问！
    iota(st.begin(),st.end(),0);
    //贪心
    for(int it:k){
        vector<int>ls(st.begin(),st.begin()+it);//取出前k个盘子
        for(int it2:ls)cnt[it2]++;//次数++
        sort(ls.begin(),ls.end(),[&](int a,int b){return cnt[a]<cnt[b];});//贪心的必要排序
        for(int i=0;i<it;i++) st[i]=ls[i];
    }
    int mx=*max_element(cnt.begin(),cnt.end());//stl太厉害了，可以直接用内置函数求出最大值（快学学！）
    cout<<mx;
	return 0;
    //完结撒花！
}
```
完结撒花！