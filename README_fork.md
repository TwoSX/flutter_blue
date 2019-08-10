

### 读取信号强度

实现蓝牙设备连接成功后，读取设备信号强度

Android 和 iOS 都已实现

方法：**`BluetoothDevice#redRssi()`**

例子：
```dart
device.redRssi().then((rssi) {
        print("信号强度: $rssi");
      }, onError: (e) {
        print(e);
      });
```

如果需要监听信号强度变化，可使用定时器获取数据。例子：

```dart
Timer _timer = Timer.periodic(const Duration(milliseconds: 1000), (timer) {
      device.redRssi().then((rssi) {
        print("信号强度: $rssi");
      }, onError: (e) {
        print(e);
        timer.cancel();
      });
    });

// 注意需要手动停止定时器
_timer.cancel();
```
