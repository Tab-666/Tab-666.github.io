搬运我的洛谷题解，原文创作时间：2026-03-05 17:04。

# 思路：
比较简单的一道题，可以找输入的每个单词中每个位置出现字符最多的字符，组成一个新单词，然后记录每个单词和新单词不同的字符数量的总和，最后输出总和即可。
# 代码：
```cpp
#include<bits/stdc++.h> 
using namespace std;
int n,M;
int main(){
    cin>>n>>M;
    vector<string>ar;
    for(int i=1;i<=n;i++){
        string cun;
        cin>>cun;
        ar.push_back(cun);
    }
    string mubiao="";
    for(int i=1;i<=M;i++){
        map<char,int>m;
        for(int k=0;k<n;k++){
            char z=ar[k][i-1];
            m[z]++;
        }
        int mxs=-999;
        char mxf;
        for(auto it:m){
            if(it.second>mxs){
                mxf=it.first;
                mxs=it.second;
            }
        }
        mubiao+=mxf;
    }    
    int cnt=0;
    for(int i=0;i<ar.size();i++){
        for(int j=0;j<ar[i].size();j++){
            if(ar[i][j]!=mubiao[j]){
                cnt++;
            }
        }
    }
    cout<<cnt;
	return 0; 
}
```