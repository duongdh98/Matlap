# _MatLap mini projects_

## 1. [Function in matylap](#1)

#

## <a id="1"></a>1. Function in Matlap

```sh
    x = 3;
    y = 2;
    z = perm(x,y);
    fprintf("matlap script %d", z);

    function p = perm(n,r)
        p = fact(n)/fact(n-r);
    end

    function f = fact(n)
        f = prod(1:n);
    end
```