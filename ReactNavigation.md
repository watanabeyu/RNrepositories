# React Navigation Technique

## Dynamically change navigationOptions
```jsx
export default class Screen extends React.Component {
  static navigationOptions = ({ navigation }) => {
    const { state, setParams } = navigation;
    const { params } = navigation.state;

    return {
      headerTitle: (
        <View>
          <TouchableOpacity onPress={(params && params.onHeaderTitleClick) ? params.onHeaderTitleClick : null}>
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
