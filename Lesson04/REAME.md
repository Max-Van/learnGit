# This is heading 1
==============


# This is leading 2 

### This is leading 2.1

### This is leading 2.2 

This is **bold** line. 
This is anotehr **italic** line. 
This is  ***bold and italic*** line. 

This is `line with background`. 

This is [apple official website](https://www.apple.com.cn). 

This is list :

* item 1 
* item 2
* item 3 

This is list with hyper link :

* [Sina](https://www.sina.com.cn)
* [Sohu](https://www.sohu.com)


this is a image : 

![lovely smile](https://cdn-std.dprcdn.net/files/acc_136293/wv0sb8)


This is linux command 

~~~bash
$ git config --global user.name 'fan'
$ git config --global user.email 'maxffq@me.com'
~~~

This is python code 

~~~python
import argparse
# [START auth_http_implicit]
def implicit():
    import google.auth
    from google.auth.transport import requests

    # Get the credentials and project ID from the environment.
    credentials, project = google.auth.default(
        scopes=['https://www.googleapis.com/auth/cloud-platform'])

    # Create a requests Session object with the credentials.
    session = requests.AuthorizedSession(credentials)

    # Make an authenticated API request
    response = session.get(
        'https://www.googleapis.com/storage/v1/b'.format(project),
        params={'project': project})
    response.raise_for_status()
    buckets = response.json()
~~~

This is blockquotes: 

> Knowledge is power. 
> ——Bacon

Quote break.

> 天下为公
> 孙文
 

 Three or more...

---

Hyphens

***

Asterisks

___


[![IMAGE ALT TEXT HERE](https://cdn-std.dprcdn.net/files/acc_136293/49XXca)](https://www.youtube.com/watch?v=I1OO6WaxqEg)