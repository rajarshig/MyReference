## IO
The python [IO](https://docs.python.org/3/library/io.html) module provides numerous way to handle text, binary & raw data.

## Get filename & extension
```
name, ext = os.path.splitext('file.txt')
```

## Get absolute path of a file
```
filepath = 'folder1/folder2/test.csv'
absolute_file_path = os.path.join(os.path.dirname(os.path.realpath(__name__)), filepath)
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
