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
Should you delete `borderRadius` or `borderBottomWidth`.

## Delete TextInput underline
```jsx
<TextInput underlineColorAndroid="transparent" />
```

## Fetch request_headers becomes lowercase
```js
// on Android
Fetch("https://xxxxxxxx",{
  method: "get",
  headers: {
    "Accept": "application/json, */*",
    "Authorization": "Bearer tokenishere"
  }
}).then(response => console.log(response))
```
```json
// on Server
header:{
  "accept": "application/json, */*",
  "authorization": "Bearer tokenishere"
}
```
Android fetch is send add header to lowercase.  
Should you correspond lowercase header on server.  
**HTTP headers are case insensitive.**
