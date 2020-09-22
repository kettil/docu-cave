# Nginx


## Redirect with `map`

File with the forwarding rules

```nginx
# Path: /etc/nginx/conf.d/example.map
#
# A line must be terminated with a semicolon
#

# direct allocation

/old/path	      /new/path;
/other/old/path /other/new/path;

# Regex

~^/old_path(?<suffix>.*)$       /new_path$suffix;
#  /old_path      => /new_path
#  /old_paths     => /new_paths
#  /old_path/sub  => /new_path/sub

~^/old_path(?<suffix>/.*|)$     /new_path$suffix;
#  /old_path      => /new_path
#  /old_paths     => <rule does not apply>
#  /old_path/sub  => /q1wert/sub

~/(?<lang>(en|de|fr))/oldname   /$lang/newname;
#  /en/oldname    => /en/newname
#  /de/oldname    => /de/newname
#  /fr/oldname    => /fr/newname
```

Server configuration

```nginx
map $request_uri $redirect_example {
    # load redirect file
    include /etc/nginx/conf.d/example.map;
}

server {
    # ...

    # redirect handling
    if ($new_blog_uri) {
        return 302 $new_blog_uri;
    }

    # ...

    location / {

        # ...

    }
}

```
