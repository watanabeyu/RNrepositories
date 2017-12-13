# React Navigation Technique

## Dynamically change navigationOptions
```jsx
export default class Screen extends React.Component {
  static navigationOptions = ({ navigation }) => {
    const { params = {} } = navigation.state;

    return {
      headerTitle: (
        <View>
          <TouchableOpacity onPress={params.onHeaderTitleClick}>
            <Text>{(params && params.title) ? params.title : "initial"}</Text>
          </TouchableOpacity>
        </View>
      ),
    }
  }
  
  componentWillMount() {
    this.props.navigation.setParams({
      onHeaderTitleClick: this.onHeaderTitleClick
    });
  }

  onHeaderTitleClick = (e) => {
    this.props.navigation.setParams({ "title": "dynamically header title text" });
  }
}
```

## Reset to root on Nesting Navigators
```jsx
this.props.navigation.dispatch(NavigationActions.reset({
  index: 0,
  key: null,
  actions: [
    NavigationActions.navigate({ routeName:"route" })
  ],
}));
```
