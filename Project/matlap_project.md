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

#
```sh
function lib()
    % ===== Get mode module =====
    mode = get_mode_module();
    switch mode
        case 1
            op_name = open_module();
            op_block_of_module(op_name);
        case 2
            new_name = create_new_module();
            op_block_of_module(new_name);
        otherwise
    end
end 

function create_module(name)
    if isfile(name)
        fprintf(">>> File exist. \n");
        open_system(name);
    else
        fprintf(">>> File does not exist. \n");
        new_system(name);
        open_system(name);
    end
end

function add_blocks_module()
    add_block("simulink/Sources/Sine Wave", "my_module/Sine", "Position", [10 10 70 70]);
    add_block("simulink/Sources/Pulse Generator", "my_module/Pulse", "Position", [10 90 70 160]);
    add_block("simulink/Math Operations/Add", "my_module/Add", "Position", [200 10 270 70]);
    %add_block("simulink/Sources/Pulse Generator", "my_module/Pulse", "Position", [185 350 215 380]);
end

% ===== Get mode module =========================================
function mode = get_mode_module()
    while true
        fprintf("-----MAIN MENU----- \n");
        fprintf("1. Open available module \n");
        fprintf("2. Create module \n");
        mode = input("Select mode: ");
        switch mode
            case 1
                break;
            case 2
                break;
            otherwise
                fprintf("Unavailable selection, try again: \n");
        end
    end
end

% ===== mode module 1 =========================================
function name_module = open_module()
    name_module = input("Simulink System : ", "s");
end

% ===== mode module 2 =========================================
function name_module = create_new_module()
    name_module = input("Name module : ", "s");
end

% ===== option block of module ================================
function select = op_block_of_module(name)
    while true
        fprintf("Simulink System: %s \n", name);
        fprintf("-----MAIN MENU-----\n");
        fprintf("1. Add Block\n");
        fprintf("2. Delete Block\n");
        fprintf("3. Connect Block\n");
        fprintf("4. Delete Line\n");
        fprintf("5. Display Block Info\n");
        fprintf("6. Exit\n");
        select = input("Select mode:");
        switch select
            % === Add block =====================
            case 1
                add_block();
                break;
            % === Delete block ===================
            case 2
                break;
            % === Connect block ==================
            case 3
                break;
            % === Delete Line ====================
            case 4
                break;
            % === Display Block Info =============
            case 5
                break;
            % === Exit ===========================
            case 6
                break;
            otherwise
                fprintf("Unavailable selection, try again: \n");
        end
    end
end

% ===== Add Block ========================================
function select_add = add_block()
    fprintf("-----ADD BLOCK MENU-----\n");
    fprintf("1. Chose path\n");
    fprintf("2. Add New Block\n");
    fprintf("3. Exit\n");
    select_add = input("Select mode:");
    switch select_add
        case 1
            add_block_chose_path();
        case 2
            add_block_new();
        case 3
            add_block_exit();
        otherwise
            add_block();
    end
end
% ===== <Add Block> Chose pahth ==========================
function add_block_chose_path()
end
% ===== <Add Block> Add New block ========================
function add_block_new()
end
% ===== <Add Block> Exit =================================
function add_block_exit()
end

% ===== Delete Block =====================================
function select_del = delete_block()
    fprintf("-----DELETE BLOCK MENU-----\n");
    fprintf("1. Chose path\n");
    fprintf("2. Add New Block\n");
    fprintf("3. Exit\n");
    select_del = input("Select mode:");
    switch select_del
        case 1
            del_block_chose_path();
        case 2
            del_block_delete();
        case 3
            del_block_exit();
        otherwise
            delete_block();
    end
end
function del_block_chose_path()
end
% ===== <Add Block> Add New block ========================
function del_block_delete()
end
% ===== <Add Block> Exit =================================
function del_block_exit()
end

% ===== Connect Block ====================================
% ===== Delete Line ======================================
% ===== Display Block Info ===============================
% ===== Exit =============================================

```