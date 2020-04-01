---
title: 键值对container.Map
date: 2020-03-18 11:12:43
categories: 
- Matlab
- Matlab知识点
---

# 键值对container.Map

## 初始化方法：

```
M = containers.Map(keySet,valueSet)
M = containers.Map(keySet,valueSet,'UniformValues',isUniform)
M = containers.Map('KeyType',kType,'ValueType',vType)
M = containers.Map

'UniformValues'为valueSet 中的统一值的指示符，表示valueSet中的类型必须一致，
指定为 true (默认) 或 false。
```
```
keySet = {'Jan','Feb','Mar','Apr'};
valueSet = [327.2 368.2 197.6 178.4];
M = containers.Map(keySet,valueSet)
M = 
  Map with properties:
        Count: 4
      KeyType: char
    ValueType: double

M('Mar')
ans = 197.6000
```
## 修改元素:
```
M('Mar') = 123
M('Mar')
ans = 123
```
## 添加元素:
```
M('anker') = 1024
M.Count
ans = 5
```
## 删除元素：
```
M.remove('anker') 
ans = 
  Map - 属性:
        Count: 4
      KeyType: char
    ValueType: double
```
## isKey:

```
 M.isKey('anker')或isKey(M, 'anker')
 ans = 0
```
## 返回key:
```
 keys(M)或M.keys
 ans =
  1×4 cell 数组
    {'Apr'}    {'Feb'}    {'Jan'}    {'Mar'}  
```
## 返回value:
```
values(M)或M.values
ans =
  1×4 cell 数组
    {[178.4000]}    {[368.2000]}    {[327.2000]}    {[123]} 
```
