# 将一段字符串转换为驼峰格式的两种方式


### 示例： 
将型如：“convert-to-camel-case”的字符串转换为“covertToCamelCase”, 类似的也可以稍改代码处理“convert_to_camel_case”的字符串。下面给出两种处理方式：使用常规字符串处理方式和正则表达式处理方式


### 1. 使用常规的String字符串处理函数实现
``` 
function convertToCamelCase(str) {
    var camlCaseStr='';
    var arry = str.split('-');

    for (var i=0; i< arry.length; i++) {
        if(arry[i].length >0) {
            // If item not empty, then convert the first character to upper case
            camlCaseStr += arry[i].substring(0, 1).toUpperCase() + arry[i].substring(1);
        }
    } 

    // Convert the fist character to lower case
    camlCaseStr = camlCaseStr.length > 0 ? camlCaseStr.substring(0, 1).toLowerCase() + camlCaseStr.substring(1) : camlCaseStr;

    return camlCaseStr;
} 
 ``` 


### 2. 使用正则表达式实现

``` 
function convertToCamelCase(str) {
  return str.replace(/\-[a-z]/g , function(a, b){
      return b == 0 ? a.replace('-','') : a.replace('-','').toUpperCase();
  });
} 
``` 

## 注意事项
- substring 方法用于提取字符串中介于两个指定下标之间的字符’ 
substring(start,end)

start: 必需。一个非负的整数，规定要提取的子串的第一个字符在 stringObject 中的位置。
stop: 可选。一个非负的整数，比要提取的子串的最后一个字符在 stringObject 中的位置多 1。如果省略该参数，那么返回的子串会一直到字符串的结尾。

返回一个新的字符串，该字符串值包含 stringObject 的一个子字符串，其内容是从 start 处到 stop-1 处的所有字符，其长度为 stop 减 start。

说明:
- substring 方法返回的子串包括 start 处的字符，但不包括 end 处的字符。
- 如果 start 与 end 相等，那么该方法返回的就是一个空串（即长度为 0 的字符串）。
- 如果 start 比 end 大，那么该方法在提取子串之前会先交换这两个参数。
- 如果 start 或 end 为负数，那么它将被替换为 0。 


- substr 方法用于返回一个从指定位置开始的指定长度的子字符串。 
stringObject.substr(start [, length ])

start:   必需。所需的子字符串的起始位置。字符串中的第一个字符的索引为 0。
length: 可选。在返回的子字符串中应包括的字符个数。

说明:
- 如果start为负数，则start=str.length+start。
- 如果 length 为 0 或负数，将返回一个空字符串。
- 如果没有指定该参数，则子字符串将延续到stringObject的最后。

