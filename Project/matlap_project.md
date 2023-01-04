# _MatLap mini projects_

## 1. [Function in matlap](#1)
## 2. [Function array](#2)
## 3. [Function write txt](#3)
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

## <a id="2"></a>2. Function array
```sh
    filename = 'matlap_ex.xlsx';
    M = readmatrix(filename);
    [x_matix, y_matix] = size(M);
    fprintf("size of matix x = %d, y = %d. \n", x_matix, y_matix);

    result_old = 0;
    result_even = 0;
    for i = 1:x_matix
        for j = 1:y_matix
            val = M(i,j);
            if mod(val, 2) == 0
                %fprintf("%d \t", val);
                %size_array_even = size_array_even + 1;
                %array_even(size_array_even) = val;
            elseif mod(val, 2) == 1
                %fprintf("%d \t", val);
                %size_array_old = size_array_old + 1;
                %array_old(size_array_old) = val;
            end
        end
        fprintf("\n");
    end
    fprintf("List ")
    array_even
    file = fopen('matlap_text.txt','wt');
    fprintf(file,'%s ', "Result after add: \r");
    for i = 1:length(array_even)
        fprintf(file,'%d \t', array_even(i));
    end
    fclose(file);

```

## <a id="3"></a>3. Function write txt
```sh
    filename = 'matlap_ex.xlsx';
    M = readmatrix(filename);
    [x_matix, y_matix] = size(M);
    fprintf("size of matix x = %d, y = %d. \n", x_matix, y_matix);

    result_old = 0;
    result_even = 0;
    for i = 1:x_matix
        for j = 1:y_matix
            val = M(i,j);
            if mod(val, 2) == 0
                fprintf("%d \t", val);
                result_even = result_even + val;
            elseif mod(val, 2) == 1
                fprintf("%d \t", val);
                result_old = result_old + val;
            end
        end
        fprintf("\n");
    end
    fprintf("List ")
    array_even
    array_old
    file = fopen('matlap_text.txt','wt');
    fprintf(file,'%s %d \r', "Result after add : ", result_even);
    fprintf(file,'%s %d \r', "Result after old : ", result_old);
    fclose(file);
```