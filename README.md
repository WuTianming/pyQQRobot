# pyQQRobot
基于Python3与WebQQ的QQ机器人框架。

A QQ Robot framework based on WebQQ and Python3.

## Disclaimer
As a Senior Two student(about to one in Senior Three) in China there just cannot be enough time for me to maintain the project often. I sincerely hope that there'll be coders interested to help.

## How to use?

### Verifications now can be saved
`QQRobot.save_veri` and `QQRobot.load_veri` have been implemented to save and load verification from files.

Verification files are encoded in `JSON`, contain cookies, friend list, group list and discus group list information.

### PEP8 Ready!
The newest version contains **some huge changes to names of classes and functions. Please pay attention.**

For more information on PEP8 standards, [click here](https://www.douban.com/note/134971609/).

Here is a simple example.

```python
#!/bin/usr/env python3

from qqrobot import QQClient, QQHandler


class MyHandler(QQHandler):
    def on_buddy_message(self, uin, msg):
        self.send_message(uin, "Hello, my name is pyQQRobot!")

if __name__ == '__main__':
    # you can save your verification
    # a.QR_veri()
    # a.save_veri('/the/path/to/your/verification/file')
    # a.login()

    # or load from a file instead
    a.load_veri('./my_verification.veri')
    # You don't need to fetch all that lists,
    # as they are already loaded from verfication files.
    a.login(get_info=False)
```

You can refer to src/example.py for another example, using some sort of intelligent robot to respond to messages.

## Functions
Up till now you can receive & send messages to your buddies and in groups.

Discus groups & more functions will be supported in the future.

## Structure
Here's a brief list of the files included:

* **qqrobot.py** includes
    * **QQClient** A set of WebQQ APIs and the core runtime of pyQQRobot
    * **QQHandler** The simple plugin framework.
* **qqfriends.py** The QQ friends, groups and discus groups data parser.
* **qqhttp.py** Simple HTTP Client.
* **mlogger.py** Simple screen logger.

Commonly **qqRobot** is what you all need.

## Known bugs & Possible improvements
1. ~~`retcode 103` when sending `poll2` requests.~~ Problem solved.
2. ~~Possible unhandled `404` errors can lead to crash.~~ 404 errors ignored.
3. More APIs.
4. Using `gevents` instead of `urllib` with `multiprocessing.dummy`.
5. Better `mLogger` with filtering functions.
6. ~~To save verification in files, and read them.~~