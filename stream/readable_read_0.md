
在某些情况下，需要有机制来触发刷新基础可读流， 而没有实际消费任何数据。在这种情况下，可以调用`readable.read(0)`，返回`null`。

如果内部读取缓冲区低于`highWaterMark`，并且该流目前未读取，则调用`stream.read(0)`将触发调用底层 [`stream._read()`][stream-_read]方法。

虽然大多数应用程序几乎都不需要这样做，但Node.js中会出现这种情况，尤其是在可读流类内部。

