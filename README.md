## 原理讲解

[Python实现模块热加载](https://mp.weixin.qq.com/s/dAQZidjGGQwVA3WMo9RCUA)

## 功能

热加载模块: 监听一个目录，当有py文件改变时，重新加载它

如果需要函数和方法级的热加载，请看：https://github.com/breuleux/jurigged

## 安装

pip install module-hot-loading

## 使用

```python
from threading import Event
from module_hot_loading import monitor_dir


if __name__ == "__main__":
    event = Event()
    event.set()
    path = "."
    monitor_dir(path, event, __file__, interval=2, only_import_exist=False)
```
monitor_dir的参数: 

1. 需要监控的目录路径
2. 停止监控的事件信号
3. __main__的代码文件路径
4. interval: 每隔几秒打一次文件快照做比对
5. only_import_exist: 只重新加载已经导入的模块

#### 效果

![](http://cdn.ikanade.cn/20231206110530.png)

