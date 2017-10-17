# React Native Android Hack

## Doesn't work border different width with borderRadius
```css
button:{
  backgroundColor   : "#fcc",
  borderRadius      : 8,
  borderWidth       : 1,
  borderColor       : "#f00",
  borderBottomWidth : 4
}
```
**This is not working on Android.**  
So you delete `borderRadius` or `borderBottomWidth`.

## Delete TextInput underline
```jsx
<TextInput underlineColorAndroid="transparent" />
```
