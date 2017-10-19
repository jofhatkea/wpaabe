# Wordpress as a backend
## Setup
1. Install WP

2. install [Application Passwords](https://wordpress.org/plugins/application-passwords/)

3. setup permalinks

## Post install process
3. Create a new user
  - set right to Admin/editor or author
4. Create a new "Application password" for the user
  - remember the "password"
5. run `echo -n "username:password" | base64`in the terminal, where:
  - `username` is the username, not the application password thingy
  - `password` is what you got in the previous step
6. Save the string for later
## Posting data
6. Use a different browser, or log out!!!!!
7. (optional) Create separate site, same root
8. http://v2.wp-api.org/reference/posts/

```js
function postStuff(){
       let data = {
         title: 'title'
       }
    fetch("wordpress/wp-json/wp/v2/posts", {
        method: 'POST',
        headers: {
            'Authorization': 'Basic ZGJ1c2VyOjk5OGQgWUh4bSBZVUc3IE5YS00gOUdIYSA1bGMz',
            'Content-Type': 'application/json; charset=utf-8'
        },
        body: JSON.stringify(data),
        credentials: 'same-origin'
    }).then(e=>e.json())
    .then(d=>{
        console.log("posting ", d)
    }).catch(e=>{console.log(e)});
  }
    postStuff();
```
