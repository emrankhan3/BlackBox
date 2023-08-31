
# BLACK BOX  (KALA BAXO)
## Table of contents
**[Binary Search](#Binary-Search)**<br> 
**[Bitset](#Bitset)**<br> 
**[Longest Increasing Subsequence](#LIS)**<br>
**[Maximum Xor Subarray](#Max-Xor-Subarray)**<br>

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


### LIS

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
