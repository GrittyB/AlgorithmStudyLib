 ```cpp
ll exgcd(ll a, ll b, ll &x, ll& y) { 
    if(b == 0) { x = 1, y = 0; return a;  }
    ll g = exgcd(b, a % b, x, y);
    x -= a / b * y;
    swap(x, y);
    return g;
}
```