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

## Can't style to picker text
Picker on Android, can't change text style, and itemStyle props is only iOS.  
If you want to style text, should create original picker component.  
For example below.
```jsx
<Modal visible={this.props.isVisible} animationType="slide" transparent onRequestClose={() => { }}>
  <View style={styles.container}>
    <View style={styles.buttons}>
      <TouchableOpacity style={styles.button} onPress={this.onCancel}>
        <Text style={styles.buttonText}>{this.props.cancelText}</Text>
      </TouchableOpacity>
    </View>
    <View style={styles.pickerContainer}>
      <ScrollView style={styles.pickerScroll}>
        {this.props.data.map((v, i) => (
          <TouchableOpacity onPress={(e) => this.props.onConfirm(v, i)} key={i}>
            <Text style={styles.pickerLabel}>{v.label}</Text>
          </TouchableOpacity>
        ))}
      </ScrollView>
    </View>
  </View>
</Modal>

const styles = StyleSheet.create({
  container: {
    position: 'absolute',
    left: 0,
    right: 0,
    bottom: 0
  },
  buttons: {
    backgroundColor: '#f4f4f4',
    flexDirection: 'row',
    justifyContent: 'space-between',
    borderTopWidth: 1,
    borderTopColor: '#cdcdcd'
  },
  button: {

  },
  buttonText: {
    fontSize: 15,
    paddingTop: 13,
    paddingBottom: 13,
    paddingLeft: 10,
    paddingRight: 10,
    color: '#5492fe',
    fontWeight: 'bold'
  },
  pickerContainer: {
    backgroundColor: '#d2d5da',
  },
  pickerScroll: {
    flex: 1,
    maxHeight: 180
  },
  pickerLabel: {
    padding: 10,
    color: "#333"
  }
});
```
