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
    % ===== Get mode module =====================================
    % >>> Global values =========================================
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

% ===== Get mode module ========================================
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
    %name_module = input("Simulink System : ", "s");
    name_module = "my_module";
end

% ===== mode module 2 =========================================
function name_module = create_new_module()
    name_module = input("Name module : ", "s");
end

% ===== option block of module ================================
function select = op_block_of_module(name_block)
    while true
        fprintf("Simulink System: %s \n", name_block);
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
                add_block(name_block);
                break;
            % === Delete block ===================
            case 2
                delete_block(name_block);
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
function select_add = add_block(name)
    fprintf("-----ADD BLOCK MENU-----\n");
    fprintf("1. Chose path\n");
    fprintf("2. Add New Block\n");
    fprintf("3. Exit\n");
    select_add = input("Select mode:");
    switch select_add
        case 1
            add_block_chose_path(name);
        case 2
            add_block_chose_path(name);
        case 3
            add_block_exit();
        otherwise
            add_block();
    end
end
% ===== <Add Block> Chose pahth ==========================
function add_block_chose_path(name)
    load_system(name);
    open_system(name);
    arr_path_add = find_system(name)
    [size_add_row, size_add_col] = size(arr_path_add);
    curr_chose = sub_chose_path(size_add_row);
    path_cv = string(arr_path_add(curr_chose, 1));
    add_block_new(path_cv);
end

function current_chose = sub_chose_path(max_chose)
    while true
        current_input = input("Chose path : ");
        if current_input <= max_chose
            break;
        end
    end
    current_chose = current_input;
end

% ===== <Add Block> Add New block ========================
function add_block_new(path_bl)
    simulink_check = ["BlockType", "Name"];
    while true
        block_type = input("Block Type : ", "s");
        load_system("simulink");
        result_block = find_system("simulink", simulink_check(1), block_type)
        [x, y] = size(result_block);
        
        if x > 0
            block_name = input("Block Name : ", "s");
            val_block = string(result_block(1, 1));
            path_full = strcat(path_bl,"/", block_name);
            path_simul = strrep(val_block, newline, ' ');
            func_add_block(path_simul, path_full);
            break;
        else
            result_block = find_system("simulink", simulink_check(2), block_type);
            [x, y] = size(result_block);
            if x > 0
                block_name = input("Block Name : ", "s");
                val_block = string(result_block(1, 1));
                path_full = strcat(path_bl,"/", block_name);
                path_simul = strrep(val_block, newline, ' ');
                func_add_block(path_simul, path_full);
                break;
            end
        end
        %block_name = input("Block Name : ", "s");
        %path_source = strcat(path_source,"/", block_type)
        %path_dest   = strcat(path_dest, "/", block_name)
    end
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