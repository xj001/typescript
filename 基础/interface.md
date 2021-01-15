# 接口

不需要按照顺序出现，但是需要全部实现

```typescript
interface LabelString{
	label:string;
}
let obj:Labelstring = {
	label:"tag"
}
```

## 可选属性

```typescript
interface LabelString{
	label?:string;
}
```

## 只读属性

```typescript
interface LabelString{
	readonly label?:string;
}
```

const和readonly区别在于一个是属性，一个是变量

## 多余属性

```typescript
interface LabelString{
	label:string;
}
let obj:Labelstring;

// 会报错
obj = {
	label:"tag",
	name:"xx"
};
// 解决方案一
obj = {
	label:"tag",
	name:"xx"
} as Labelstring;

// 解决方案二
interface LabelString{
	label:string;
  // 索引
  [propName:string]:any;
}
```

## 函数

```typescript
interface SearchFunc{
	(source:string,substring:string):boolean;
}
let mySearch:SearchFunc;
mySearch = function(src,sub){
  return true;
}
```

## 索引签名

支持字符串和数字

```typescript
interface NumberDictionary{
  [index:string]:number;
  length:number;
  // 报错，原因，name是string类型index，属性值应该是number
  name:string;
}

// 解决办法
interface NumberDictionary{
  [index:string]:number | string;
  length:number;
  name:string;
}
```

## 类类型

```typescript
interface PersonInterface{
  name:string;
}
class Person implements PersonInterface{
  name:string;
}
```

## 接口扩展

```typescript
interface Shape{
  color:string;
}
interface PenStroke {
  penWidth: number;
}

interface Square extends Shape, PenStroke {
  sideLength: number;
}
```

## 混合类型

```typescript
interface Counter {
  (start: number): string;
  interval: number;
  reset(): void;
}

function getCounter(): Counter {
  let counter = function (start: number) {} as Counter;
  counter.interval = 123;
  counter.reset = function () {};
  return counter;
}
```

