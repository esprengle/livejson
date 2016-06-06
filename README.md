# `livejson`
A Python library implementing a `dict`-like object that writes to a file as it is modified

`livejson` is:

- **Easy**: use `livejson` with the same interface as Python `list`s and `dict`s, meaning it can basically be used as a drop-in replacement.
- **Flexible**: `livejson` fully supports complex nestings of `list`s and `dict`s, meaning it can represent any valid JSON file.
- **Compatible**: `livejson` works perfectly on both Python 2 and Python 3.
- **Lightweight**: `livejson` is a single file with no external dependencies. Just install and go!
- **Reliable**: no caching is used. Every single time you access a `livejson.Database`, it's read straight from the file. And every time you write to it, the change is instant. No delays, no conflicts.

`livejson` can be used for:

- **Database storage**: you can use `livejson` to easily write flexible JSON databases, without having to worry about complex `open` and `close` operations, or learning how to use the `json` module.
- **Debugging**: You can use `livejson` to back up your Python objects. If you use a `livejson.Database` instead of a `dict` or a `list` and your script crashes you'll still  have a hard copy of your object. And you barely had to change any of your code.
- **General-purpose JSON**: If your script or application needs to interact with JSON files in any way, consider using `livejson`, for simplicity's sake. `livejson` can make your code easier to read and understand, and also save you time. 

Thanks to [dgelessus](https://github.com/dgelessus) for naming this project.

## Installing
`livejson` supports both Python 2 and 3, and can be easily installed with `pip`.
```bash
# Python 2
sudo pip install livejson
# Python 3
sudo pip3 install livejson
```
After installing, you can just `import livejson` from your code!

## Example usage
Creating a new database:
```python
>>> import livejson
>>> my_db = livejson.Database("test.json")
>>> my_db["dogs"] = "cats"
>>> with open("test.json", "r") as f:
...     print(f.read())
...
{"dogs": "cats"}
>>> my_db["dogs"]
'cats'
```
Reading and modifying an existing database:
```python
>>> my_db = livejson.Database("test.json")
>>> my_db["dogs"]
u'cats'
>>> my_db["dogs"] = "fish"
>>> with open("test.json", "r") as f:
...     print(f.read())
...
{"dogs": "fish"}
>>>
```
