先引入库
```python
import os
```
然后
```python
os.path.split(os.path.realpath(__file__))[0]  # 返回 string
```

