# 将一段字符串转换为驼峰格式的两种方式


### 示例： 
将型如：“convert-to-camel-case”的字符串转换为“covertToCamelCase”, 类似的也可以稍改代码处理“convert_to_camel_case”的字符串。下面给出两种处理方式：使用常规字符串处理方式和正则表达式处理方式


### 1. 使用常规的String字符串处理
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
}```

### 2. 使用正则表达式处理 

'''
function convertToCamelCase(str) {
  return str.replace(/\-[a-z]/g , function(a, b){
      return b == 0 ? a.replace('-','') : a.replace('-','').toUpperCase();
  });
}
'''
