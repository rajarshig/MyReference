# Get filename & extension
```
name, ext = os.path.splitext('file.txt')

```

## numpy value to json custom encoder
```
import numpy
import json

class MyEncoder(json.JSONEncoder):
    def default(self, obj):
        if isinstance(obj, numpy.integer):
            return int(obj)
        elif isinstance(obj, numpy.floating):
            return float(obj)
        elif isinstance(obj, numpy.ndarray):
            return obj.tolist()
        else:
            return super(MyEncoder, self).default(obj)

You use it like this:

json.dumps(numpy.float32(1.2), cls=MyEncoder)
json.dumps(numpy.arange(12), cls=MyEncoder)
json.dumps({'a': numpy.int32(42)}, cls=MyEncoder)

```