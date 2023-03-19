
# CP note

I'll add various/random codes/notes here


## 1) Bitset

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


## 2) LIS

### Longest Increasing Subsequnce n(log(n))

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

