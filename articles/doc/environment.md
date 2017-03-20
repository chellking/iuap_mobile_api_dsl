# $environment
$environment是一个可以获取设备系统类型的全局对象。通过$environment提供不同的变量，来获判断设备的系统。

## $environment.DeviceAndroid
$environment.DeviceAndroid变量的值为android

**语法**```$environment.DeviceAndroid```

**参数***无*

## $environment.DeviceIOS
$environment.DeviceIOS变量的值为ios

**语法**```$environment.DeviceIOS
```

**参数***无*

## $environment.DeviceType
&emsp;&emsp;$environment.DeviceType变量的值为返回设备的系统ios||android

**语法**```$environment.DeviceType```

**参数***无*

**实例**
```
if (environment.DeviceType == environment.DeviceIOS) { // 您的代码逻辑}if (environment.DeviceType == environment.DeviceAndroid) { // 您的代码逻辑}
```
