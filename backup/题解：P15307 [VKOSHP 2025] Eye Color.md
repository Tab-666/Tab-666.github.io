搬运我的洛谷题解，原文创作时间：2026-02-14 21:28。

# 思路：
这道题是纯模拟题，根据题意解即可。

直接上代码。
# 代码：
考虑到我的题解思路部分好像不够多，于是我在代码里加了亿点注释！

::::info[代码]
```cpp
//考虑到我的题解思路部分好像不够多，于是我在代码里加了亿点注释！
#include <bits/stdc++.h>
using namespace std;
int main(){
    string biao[4]={"blue","brown","green"};//基础表
    string p1,p2,c;//p1是父亲的眼睛颜色，p2是母亲的，c是后代的。
    cin>>p1>>p2>>c;//输入
    vector<vector<string>>r;//用于记录正确结果
    //由于只有三种眼色，所以直接暴力三重循环求解，暴力出奇迹！
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            for(int k=0;k<3;k++){
                string a=biao[i],b=biao[j],ch=biao[k];
                if((p1=="."||a==p1)&&(p2=="."||b==p2)&&(c=="."||ch==c)&&((a=="brown"||b=="brown")?ch=="brown":(a=="green"||b=="green")?ch=="green":ch=="blue")){//判断
                    r.push_back({a,b,ch});//符合条件加入结构集
                }
            }
        }
    }
    //来个排序
    sort(r.begin(),r.end());
    //如果无正确结构则输出Incorrect
    if(r.empty()) cout<<"Incorrect";
    else{
        //否则则遍历结果集输出
        for(auto it:r){
            cout<<it[0]<<" "<<it[1]<<" "<<it[2]<<endl;
        }
    }
    return 0;
}
```