
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
**[Binary Indexed Tree](#Binary-Indexed-Tree)**<br>
**[Disjoint Set Union](#Disjoint-Set-Union)**<br> 
**[Knapsack 2D](#Knapsack-2D)**<br> 
**[Longest Increasing Subsequence](#LIS)**<br>
**[Maximum Xor Subarray](#Max-Xor-Subarray)**<br>
**[Segment Tree](#Segment-Tree)**<br>
**[Segment Tree Lazy Propagation](#Segment-Tree-Lazy-Propagation)**<br>
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


<details>
<summary>How do I dropdown?</summary>
<br>#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define wt getchar();
#define ttt cerr<<"T"<<endl;
#define dbg1(x) cerr<<#x<<": "<<x<<endl;
#define dbg2(x,y) cerr<<#x<<": "<<x<<", "<<#y<<": "<<y<<endl;
#define dbg3(x,y,z) cerr<<#x<<": "<<x<<", "<<#y<<": "<<y<<", "<<#z<<": "<<z<<endl;
#define dbg4(x,y,z,xx) cerr<<#x<<": "<<x<<", "<<#y<<": "<<y<<", "<<#z<<", "<<z<<", "<<#xx<<": "<<xx<<endl;
#define old ios::sync_with_stdio ( 0 );cin.tie ( nullptr );cout.tie (nullptr );

// #define inf 1000000000000000005

#include<bits/stdc++.h>

#include<ext/pb_ds/assoc_container.hpp>
#include<ext/pb_ds/tree_policy.hpp>

using namespace std;
using namespace __gnu_pbds;

typedef tree<int, null_type, greater<int>, rb_tree_tag, tree_order_statistics_node_update> pbds; // find_by_order, order_of_key

template<class key, class value, class cmp = std::less<key>>
using ordered_map = tree<key, value, cmp, rb_tree_tag, tree_order_statistics_node_update>;
#define fo(i,a,b) for(i=a;i<=b;i++)
#define all(v) (v).begin(),(v).end()
#define all1(v) (v).begin()+1,(v).end()
#define allr(v) (v).rbegin(),(v).rend()
#define allr1(v) (v).rbegin()+1,(v).rend()
#define ty int t; cin >> t; while(t--)
#define tcs(x) cout<<"Case "<<x<<": ";
#define ts cerr<<"TTTT"<<endl;
#define ty int t; cin >> t; while(t--)
#define pb push_back
#define umap unordered_map
#define uset unordered_set
#define lb lower_bound
#define ub upper_bound
#define visar(x) for(int i:x) cerr<<i<<" "; cerr<<endl;
#define v2dar(n,m,ar) for(int i=0;i<n;i++){for(int j=0; j<m;j++)cout<<ar[i][j]<<" ";cout<<'\n';

// const int mod = 998244353, MAX = 3000005, INF = 1 << 30;
template <typename Ta>
void ddd ( Ta a )
{
    dbg1 ( a )
}
template <typename Ta, typename tb>
void ddd ( Ta a, tb b )
{
    dbg2 ( a, b )
}
template <typename Ta, typename tb, typename tc>
void ddd ( Ta a, tb b, tc c )
{
    dbg3 ( a, b, c )
}
template <typename Ta, typename tb, typename tc, typename td>
void ddd ( Ta a, tb b, tc c, td d )
{
    dbg4 ( a, b, c, d )
}

template <typename Ta>
Ta min ( Ta a, Ta b, Ta c ) {return min ( a, min ( b, c ) );}
template <typename Ta>
Ta min ( Ta a, Ta b, Ta c, Ta d ) {return min ( a, min ( b, c, d ) );}
template <typename Ta>
Ta max ( Ta a, Ta b, Ta c ) {return max ( a, max ( b, c ) );}
template <typename Ta>
Ta max ( Ta a, Ta b, Ta c, Ta d ) {return max ( a, max ( b, c, d ) );}
const ll mod = 1e9 + 7;

const ll eps  = 1e-9 ;
const ll maxn = 4e5 + 5;
const ll inf  = 5e18 ;
const ll minf = -inf ;

ll inv ( ll i ) {if ( i == 1 ) return 1; return ( mod - ( ( mod / i ) * inv ( mod % i ) ) % mod ) % mod;}

ll mod_mul ( ll a, ll b ) {a = a % mod; b = b % mod; return ( ( ( a * b ) % mod ) + mod ) % mod;}

ll mod_add ( ll a, ll b ) {a = a % mod; b = b % mod; return ( ( ( a + b ) % mod ) + mod ) % mod;}



ll gcd ( ll a, ll b ) { if ( b == 0 ) return a; return gcd ( b, a % b );}

ll ceil_div ( ll a, ll b ) {return a % b == 0 ? a / b : a / b + 1;}
ll pwr ( ll a, ll b )
{
    a %= mod;
    ll res = 1;

    while ( b > 0 ) {if ( b & 1 ) res = res * a % mod; a = a * a % mod; b >>= 1;}

    return res;
}



void rd ( ll &a )
{
    scanf ( "%lld", &a );
}
int Bexpo ( int b, int p )
{
    int a = 1;

    if ( p == 0 ) { return 0; }

    while ( p > 0 ) {
        if ( p & 1 ) {
            a *= b;
            a %= mod;
        }

        p >>= 1;
        b *= b;
        b %= mod;
    }

    return a;
}



class dsu{
      vector<ll>p,sz,mx,mn;
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
      int get(int x){
            if(p[x]==x)return x;
            return p[x]=get(p[x]);
      }
      int findMin(int x){
            return mn[get(x)];
      }

      int findMax(int x){
            return mx[get(x)];
      }
      int s(int x){
            return sz[get(x)];
      }
      bool _union(int a,int b){
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

int m[200005];

int32_t main()
{

#ifdef emran
    ifstream cin ( "input.txt" );
    ofstream cout ( "output.txt" );
#endif
    old


      function<void ( int ) > kick = [&] ( int qwer ) {
            ll a,b,n,k,value;
            cin>>n>>k;
            vector<int>v[n+1];
            for (int i=1; i<=n; i++ )
            {
                  
                m[x]=0
            }
            for (int i=1; i<=k; i++ )
            {
                int x;
                cin >> x;
                m[x]=1;
            }
            for (int i=2; i<=n; i++ )
            {
                int x,y;
                cin >> x>>y;
                  v[x].pb(y);
                  v[y].pb(x);
            }
            int l=1, r=n;
            int ans=n-1;
            while(l<r){
                  int mid = (l+r)/2;
                  int d = 1;
                  function<
            }


      };
ty
    kick ( 6 );

}

</details>


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
### Binary Indexed Tree
```cpp
     
ll prex[200005]; // prefix sum array
ll tre[200005]; // BIT Tree
class bit{
/*
      How to use
      create a bit object e.g:   bit btree(array,size_of_ar);
      get sum using btree.sum(leftIdx,rightIdx)
      update using btree.update(idx,value)
*/
public:
      bit(ll ar[],ll n){
            // calculating prefix
            for(int i=1;i<=n; i++){
                 prex[i]=prex[i-1]+ar[i];
            }
            // creating tree with
            for(int i=1; i<=n; i++){
                  int ii = i;
                  int jj = i-(i&-i)+1;
                  tre[i]+=prex[ii]-prex[jj-1];
            }
      }
      void update(int idx,ll v){
            while(idx<200000){
                  tre[idx]+=v;
                  idx+=idx&-idx;
            }
      }
      ll s(int i){
            ll ss=0;
            while(i>0){
                //  dbg1(i)
                  ss+=tre[i];
                  i-=(i&-i);
            }
            return ss;
      }
      ll sum(int i,int j){
           // dbg1(i)
            return s(j)-s(i-1);
      }
};


```
### Segment Tree
```cpp
     
ll t[300005];
ll a[200005];
int n;
void build(int v, int tl, int tr) {
    if (tl == tr) {
        t[v] = a[tl];
    } else {
        int tm = (tl + tr) / 2;
        build( v*2, tl, tm);
        build( v*2+1, tm+1, tr);
        t[v] = t[v*2] + t[v*2+1];
}}
init(){build(1,1,n);}     //Initialization
ll sum(int v, int tl, int tr, int l, int r) {
    if (l > r)
        return 0ll;
    if (l == tl && r == tr) {
        return t[v];
    }
    int tm = (tl + tr) / 2;
    return sum(v*2, tl, tm, l, min(r, tm))
           + sum(v*2+1, tm+1, tr, max(l, tm+1), r);
}
ll query(int l, int r){return sum(1,1,n,l,r);} // sum between l-r range
void update(int v, int tl, int tr, int pos, int new_val) {
    if (tl == tr) {
        t[v] = new_val;
    } else {
        int tm = (tl + tr) / 2;
        if (pos <= tm)
            update(v*2, tl, tm, pos, new_val);
        else
            update(v*2+1, tm+1, tr, pos, new_val);
        t[v] = t[v*2] + t[v*2+1];
    }
}
void update(int idx, int v){update(1,1,n,idx,v);} // update value at index idx 

```

### Segment Tree Lazy Propagation
```cpp
     #define mx 100005
// const int mod = 998244353, MAX = 3000005, INF = 1 << 30;


ll n;
ll arr[mx];
struct info {
    ll prop, sum;
} tree[mx * 4];

void init(int node, int b, int e)
{
    if (b == e) {
        tree[node].sum = arr[b];
        return;
    }
    int Left = node * 2;
    int Right = node * 2 + 1;
    int mid = (b + e) / 2;
    init(Left, b, mid);
    init(Right, mid + 1, e);
    tree[node].sum = tree[Left].sum + tree[Right].sum;
}
void init(int a,int b){
      init(1,a,b);
}

void update(int node, int b, int e, int i, int j, ll x)
{
    if (i > e || j < b)
        return;
    if (b >= i && e <= j)
    {
        tree[node].sum += ((e - b + 1) * x);
        tree[node].prop += x;
        return;
    }
    int Left = node * 2;
    int Right = (node * 2) + 1;
    int mid = (b + e) / 2;
    update(Left, b, mid, i, j, x);
    update(Right, mid + 1, e, i, j, x);
    tree[node].sum = tree[Left].sum + tree[Right].sum + (e - b + 1) * tree[node].prop;
}
void update(int a,int b,int v){
      update(1,1,n,a,b,v);
}

ll query(int node, int b, int e, int i, int j, ll carry = 0)
{
    if (i > e || j < b)
        return 0;

    if (b >= i and e <= j)
        return tree[node].sum + carry * (e - b + 1);

    int Left = node << 1;
    int Right = (node << 1) + 1;
    int mid = (b + e) >> 1;

    ll p1 = query(Left, b, mid, i, j, carry + tree[node].prop);
    ll p2 = query(Right, mid + 1, e, i, j, carry + tree[node].prop);

    return p1 + p2;
}
ll query(int i,int j){
      return query(1,1,n,i,j,0);
}

```

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

