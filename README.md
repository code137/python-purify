# Python Purify

## Installation

```python
pip install python_purify
```

or:
``` python
python setup.py install
```

## Examples

### Setup

```pyton
from python_purify import WordPurify
from python_purify import ImagePurify
...
purify = WordPurify(my_api_key)
imgpurify = ImagePurify(my_img_api_key)
```

The Web Purify default response type is XML, but JSON is normally better to work with. We made
JSON the standard format for our package, but you can set it to XML with the rspformat variable:
```python
purify = WordPurify(my_api_key, rspformat='xml')
```
This will return a cElementTree object. If you want to use a better package like beautiful soup, you can
return the tree back to text with the following:
```python
from xml.etree import cElementTree as ET
...
out = purify.check('Some nice words')
xml_string = ET.tostring(out)
# Some other XML parser can load the data now.
```

####Initialization options:
* live - Default: True. If false, uses the webpurify sandbox
* rspformat - Default: 'json'. Can be set to 'json' or 'xml'
* verbose - Default: False. If true, prints the WebPurify url before making a request.

### WordPurify Methods
Once setup if finished, you can simply call each method:

```python
out = purify.check('Some nice words')
print out
```
The following WordPurify methods are included:
* [check](https://www.webpurify.com/documentation/methods/check/)
* [check_count](https://www.webpurify.com/documentation/methods/checkcount/)
* [replace](https://www.webpurify.com/documentation/methods/replace/)
* [wp_return](https://www.webpurify.com/documentation/methods/return/)
* [add_to_blacklist](https://www.webpurify.com/documentation/methods/addtoblacklist/)
* [add_to_whitelist](https://www.webpurify.com/documentation/methods/addtowhitelist/)
* [remove_from_blacklist](https://www.webpurify.com/documentation/methods/removefromblacklist/)
* [remove_from_whitelist](https://www.webpurify.com/documentation/methods/removefromwhitelist/)
* [get_blacklist](https://www.webpurify.com/documentation/methods/getblacklist/)
* [get_whitelist](https://www.webpurify.com/documentation/methods/getwhitelist/)

**Note** you should be able to set most of the options in the fuction call except for format. Format is determined at WordPurify creation. In this example, rsp=1 will give us the responce time and slink=1 will tell WebPurify to flag urls:
```python
purify.check('Some nice words', rsp=1, slink=1)
```

### ImagePurify Methods
**NOTE** ImagePurify is still testing

Just like with WordPurify, once setup, you can call the ImagePurify Methods.

```python
out = imgpurify.img_account()
```
The following ImagePurify methods are included:
* [img_check](https://www.webpurify.com/image-moderation/documentation/methods/imgcheck/)
* [img_status](https://www.webpurify.com/image-moderation/documentation/methods/imgstatus/)
* [img_account](https://www.webpurify.com/image-moderation/documentation/methods/imgaccount/)

### VideoPurify
coming soon

## Testing

We have written some basic tests for python 2.7. There have been no testing for python 3
