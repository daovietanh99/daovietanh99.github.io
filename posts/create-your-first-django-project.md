In this post, I will demonstrate a simple Django Web App. My tutorial focuses on the initial steps you’ll need to take to start a new web application. To start a django project, we simply use the bellow command:

```shell
python -m django-admin startproject your_project_name
```

Of course it works, but the problem with this approach is, `CTRL + click` which is normally used to open the link in the the new tab/window turns out opening the link in the same window and thus poor user experience. So to avoid this i.e. forcing it to open the link in the new tab instead of the current tab, you may want to modify your event as following:

```js
$('.someLink').on('click', function(e) {
 
    if(e.metaKey || e.ctrlKey || e.button === 1) {
        window.open('http://somelink.com/');
    }
    else {
        window.location = 'http://somelink.com/';
    }
 
});
```

It’s a little check and can greatly improve the user experience.
