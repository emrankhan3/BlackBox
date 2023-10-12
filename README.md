
# BLACK BOX  (KALA BAXO)
     ____________
    |\           |\
    |  \_________|_\
    |  |         | |
    |__|_________| |
     \ |         \ |
      \|__________\|


## Table of contents
**[Binary Search](#Binary-Search)**<br> 
**[Bitset](#Bitset)**<br> 
**[Binary Exponentiation](#Binary-Exponentiation)**<br>
**[Disjoint Set Union](#Disjoint-Set-Union)**<br> 
**[Knapsack 2D](#Knapsack-2D)**<br> 
**[Longest Increasing Subsequence](#LIS)**<br>
**[Maximum Xor Subarray](#Max-Xor-Subarray)**<br>
[template](https://docs.google.com/document/d/1lYzO9yA8irpCsG2a782awObOndtlUjAusC2iHV9Ea7E/edit#heading=h.cmhs406hkp1w)
### Bitset

#### 

| Function | return type     | Description                |
| :-------- | :------- | :------------------------- |
| set | void | Set the bit value at the given index to 1. |
|reset|void|Set the bit value at a given index to 0.|
|flip|void|Flip the bit value at the given index.|
|count|int|Count the number of set bits.|
|test|bool|takes a parameter [i] and returns 0 or 1 if [ith] given parameter is reset or set|
|_Find_first|int|return position of first set bit|
|all, any, none|bool|check all,any,none bit is set|
|to_string|string|Converts bitset to std::string.|
|to_ulong|ulong|COnverts bitset to std::ulong|


#### Disjoint Set Union
"
১. যারা পরস্পরের বন্ধু তারা সবাই একই সেটের অন্তর্গত 

২. যতগুলো সাবগ্রাফ থাকবে ততগুলো সেট থাকবে

৩. প্রতিটি সেটের একটি representative থাকবে।

৪. দুটি নোডের representativeএকই হলে তারা একই সেটে আছে। সুতরাং দুজন ব্যক্তি বন্ধু নাকি বুঝতে আমাদের তারা যে সেটে আছে তার representative চেক করতে হবে।
"
from shafaet vai er blog
```cpp
class dsu{     // class dsu, dsu mydsu(n)
      vector<ll>p,sz,mx,mn;    // p = parent, sz = size of the tree, mx = max node, mn = min node
      int n;
public:
      dsu(int n){
            for(int i=0; i<=n; i++){
                  sz.pb(1);
                  mx.pb(i);
                  mn.pb(i);
                  p.pb(i);
            }
      }
      int get(int x){          // returns the parent of the node
            if(p[x]==x)return x;
            return p[x]=get(p[x]);
      }
      int findMin(int x){     // returns the min node of the tree
            return mn[get(x)];
      }

      int findMax(int x){         // return the max node of the tree
            return mx[get(x)];
      }
      int ts(int x){               // returns the size of the tree
            return sz[get(x)];
      }
      bool _union(int a,int b){     // unites two node
            a = get(a);
            b = get(b);
            if(a==b)return false;
            if(sz[a]<sz[b])swap(a,b);
            p[b]=a;
            sz[a]+=sz[b];

            mn[a]=mn[b] = min(mn[a],mn[b]);
            mx[a]=mx[b] = max(mx[a],mx[b]);
            return true;
      }

};

```

#### Longest Increasing Subsequnce n(log(n))
```cpp
    int n;cin>>n;
    int ar[n+1]={0};

    vector<int>v;
    for (int i=1; i<=n; i++ )
    {
        int x;
        cin >> x;v.pb(x);
    }
    deque<int>dq;
    for(int i:v){
        if(dq.size()==0)dq.pb(i);
        else{
            int ind = lower_bound(dq.begin(),dq.end(),i)-dq.begin();
            if(ind==dq.size())dq.pb(i);
            else{
                dq[ind]=i;
            }
        }
    }
    cout<<dq.size()<<endl;
```
### Max Xor Subarray 
- create a VAR type variable e.g. VAR mxxorsub
- let the array with size n is arr[n],
- the max xor subarray is mxxorsub(arr,n) 
```cpp
    struct TrieNode{
        int value;
        TrieNode *child[2];
        TrieNode(){
            this->value = 0;
            this->child[0] = this->child[1] = NULL;
        }
    };

    class VAR{
    public:
        void insert(TrieNode *root,int pre_xor){
            TrieNode *temp = root;
            for(int i=31;i>=0;i--){
                bool curr  = pre_xor & (1<<i);
                if(temp->child[curr]==NULL){
                    temp->child[curr] = new TrieNode();
                }
                temp = temp->child[curr];
            }
            temp->value=pre_xor;
        }
        int query(TrieNode *root,int pre_xor){
            TrieNode *temp = root;
            for(int i=31;i>=0;i--){
                bool curr = pre_xor & (1<<i);
                if(temp->child[1-curr] != NULL){
                    temp = temp->child[1-curr];
                }else if(temp->child[curr] != NULL){
                    temp = temp->child[curr];
    
                }
            }
            return pre_xor^(temp->value);
        }
        int maxSubarrayXOR(int N, int arr[]){
            TrieNode *root = new TrieNode();
            insert(root,0);
            int result = INT_MIN,pre_xor=0;
            for(int i=0;i<N;i++){
                pre_xor= pre_xor^arr[i];
                insert(root,pre_xor);
                result = max(result,query(root,pre_xor));
            }
            return result;
        }
    };

```
### Binary Search
- lower bound of x  = l
- upper bound of x = lower bound of (x+1)
- last postion of x amoung all x = (lower bound of (x+1))-1
```cpp
        function<int(int,int,int[])> binarySearch = [](int n,int f,int arr[]){
            int l=0,r=n+1;
            while(l<r){
                  int mid = l+(r-l)/2;
                  if(arr[mid]<f){
                        l=mid+1;
                  }
                  else r=mid;
            }
            return l;
      };
```
### Segment Tree
will be added

### Binary Exponentiation
```cpp
      function<ll(ll,ll)>binExp = [](ll a, ll b){
            ll r = 1;
            while(b){
                  if(b&1){
                        r = (r*a)%mod;
                  }
                  a=(a*a)%mod;
                  b>>=1;
            }
            return r;
      };
```
### Knapsack 2D
```cpp
     
int n,w;
int nap[5][100002];
 
void knapsack()
{
 
    cin >> n >> w;
 
    int profit[n+1]={0};
    int weights[n+1]={0};
 
    for (int i = 1; i <= n; ++i)
    {
        cin >>  weights[i];
        /* code */
    }
    for (int i = 1; i <= n; ++i)
    {
        cin >>  profit[i];
        /* code */
    }
    int now,bef;
    now=1,bef=0;
    int mx=0;
    for(int i=1; i<=n; i++)
    {
        for(int j=1; j<=w; j++)
        {
            nap[now][j]=max(nap[bef][j],nap[now][j]);
            if(j>=weights[i])
            {
                int m = max(0ll,j-weights[i]);
                // nap[i][j] = max(nap[i][j],profit[i]);
 
                nap[now][j]=max(nap[now][j],profit[i]+nap[bef][m]);
                mx=max(nap[bef][j],mx);
                mx=max(nap[now][j],mx);
            }
        }
        swap(now,bef);
    }
    cout<<mx<<endl;
}

```
### bit operations
### string algos
### trie

