PushOverPy
==========

Simplistic Python Pushover API implementation not requiring more than standard libraries

Requirements
==========

Python 2.7 (have not tested on 2.6 or 3)
urllib
httplib
json
io

Optional
==========

Redis-py (to store API token & key)
xml (if you prefer XML responses, will have to write it in yourself, however)

Purpose
==========

This was written to support the full range of features that the Pushover API has.

Beyond that, it was also a side project I decided to take on.

Usage
==========

```python
import pushover

# First run with Redis installed (or if Redis is not installed, everytime)
ps = pushover('api_token', 'api_key')

# Afterwards, as long as the data is still in Redis
ps = pushover()

# To store the data in Redis afterwards
ps.store_api()

# To send a message with all defaults
ps.sendmsg('some message')

# To send a message one character at a time
ps.sendmsg('some message', blocksize=1)

# High priority
ps.sendmsg('msg', priority=1)

# Low priority
ps.sendmsg('msg', priority=-1)

# Custom timestamp ('timestamp' = Epoch value)
ps.sendmsg('msg', timestamp=0)

# Custom title for push
ps.sendmsg('msg', title='Customized Title')

# Send URL with push
ps.sendmsg('msg', url='http://www.google.com', url_title='Google Search')
```

On success, sendmsg() will return 1.  Otherwise, if there's any error messages explaining why 
it failed, that will be returned.  Lastly, if no error messages than it'll return 0.
