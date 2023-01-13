# _MatLap_

## [1. Create modules/block use script.](#1)
### [**Find path of block in simulink**](#find)
### [1.1 Add block "Sine Wave".](#11)
### [1.2 Add block "Pulse Generator"](12)
### [1.3 Add block "Add"](13)

## [2. Note](#2)
### [2.1 Delete new line in string ](#21)

#

### <a id ="find"></a>**Find path of block in simulink**
```sh
    load_system("simulink");
    find_system("simulink", "BlockType", "Scope")
```
### [1.1 Add block "Sine Wave".](#11)
## <a id = "1" ></a>1. Create modules/block use script.
- Create module
```sh
    create_module("name_module");
```
### <a id = "1" ></a>1.1 Add block "Sine Wave".
```sh
    add_block("simulink/Sources/Sine Wave", "my_module/Sine", "Position", [10 10 70 70]);
```
### <a id = "12"></a>1.2 Add block "Pulse Generator".
```sh
    add_block("simulink/Sources/Pulse Generator", "my_module/Pulse", "Position", [10 90 70 160]);
```
### <a id = "13"></a>1.3 Add block "Add".
```sh
    add_block("simulink/Math Operations/Add", "my_module/Add", "Position", [200 10 270 70]);
```

## <a id = "2"></a> 2. Note.
### <a id = "21"></a> 2.1 Delete new line in string.
```sh
    cstr = strrep(val_block, newline, ' ') 
```