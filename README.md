#Plain code for React Native UI

[Reference](https://facebook.github.io/react-native/docs/native-components-android.html)

These are the steps:
1. Create the XML (or codes) of the layout, sample is in res/layout/multiplecamerastreamlayout.xml
2. Create a View to inflate the XML(if code ignore this), sample is in com.sample_android_ui.CustomView.
3. Create a View Manager that will link the Custom View, here is the place to expose the properties. Sample is in com.sample_android_uid.MyCustomReactViewManager.
4. Create a Package and add into "createViewManager" method. Sample in com.sample_android_uid.MyCustomPackage.
5. Add the Package into MainApplication
```java
   @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
              new MyCustomPackage()
      );
    }
```
6. Define in Javascript, a custom view. Sample JS created is CustomView.js
```javascript
  //File created is named CustomView.js
  import {requireNativeComponent, ViewPropTypes} from 'react-native';
  import PropTypes from 'prop-types';

  module.exports = requireNativeComponent('MyCustomReactViewManager', null);
  //If View Manager have react properties the code will be module.exports = requireNativeComponent('MyCustomReactViewManager', {name: 'AnynameWillDoItsforLog',propTypes: { 'ReactPropName':PropTypes.* }});
```
7. Use it in the main Javascript code
```javascript
  import CustomView from './CustomView.js';
  ...
    render() {
     return
      ...
      <CustomView style={{height:200, width:200}}/>
      ...;
    }
```