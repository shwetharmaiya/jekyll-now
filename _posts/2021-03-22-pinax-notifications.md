---
layout: post
title: pinax-notifications with Django
---

**This post is an attempt to help persons who are trying to configure pinax-notifications for Django.**

While pinax-notifications at https://github.com/pinax/pinax-notifications have documented it very elaborately, there are some errors which I encountered.

1] **First error**: _RuntimeError: Model class django.contrib.sites.models.Site doesn’t declare an explicit app_label and isn’t in an application in INSTALLED_APPS._

![image](https://user-images.githubusercontent.com/3839010/112032088-06ad2b00-8b62-11eb-9965-d5c3af5273fa.png)

If you look closely, the error explains that Site is not added in INSTALLED_APPS in settings.py.

Add ‘django.contrib.sites‘ to INSTALLED_APPS in settings.py. Also, many users in StackOverflow suggest that one needs to add SITE_ID=1.

_django.core.exceptions.ImproperlyConfigured: You’re using the Django “sites framework” without having set the SITE_ID setting. Create a site in your database and set the SITE_ID setting or pass a request to Site.objects.get_current()_
is the error one gets if the SITE_ID=1 is not added into settings.py.

2] **Second error**: _. RuntimeError: Model class account.models.Account doesn’t declare an explicit app_label and isn’t in an application in INSTALLED_APPS._

![image](https://user-images.githubusercontent.com/3839010/112032381-50961100-8b62-11eb-8531-c272a6617185.png)


The error suggests that Account is not added to INSTALLED_APPS in settings.py.

Please add ‘account’ in INSTALLED_APPS in settings.py

3] Send the notification by calling send function on performing an action.

send([user], "friends_invite", {"from_user": user})

4] The result of sending notification is seen on the terminal.

![image](https://user-images.githubusercontent.com/3839010/112032500-77ecde00-8b62-11eb-9a8b-6b29b1092d41.png)

Using pinax-templates or your own templates, you can set notification emails to be sent.

For any doubts, ready to help. 

-Shwetha
