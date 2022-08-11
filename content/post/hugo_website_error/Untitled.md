# How To Resolve Hugo Error:  from config: failed to resolve output format "headers" from site config

Sometimes you might encounter the following error on typing <span style="color:DimGray;background-color: #F0FFFF">hugo server</span> from your local website directory. 

```shell
Error: from config: failed to resolve output format "headers" from site config
```

To resolve the error, head over to <span style="color:DimGray;background-color: #F0FFFF">config/_default/config.yaml</span> and temporily rewrite the following line as follows:

```shell
outputs:
  home: [RSS, JSON, WebAppManifest]
```

Open terminal and from the home directory of the website type the following commands:

```shell
hugo mod clean
hugo mod get -u ./...
hugo mod tidy
```

When the update is complete head over to <span style="color:DimGray;background-color: #F0FFFF">config/_default/config.yaml</span> and restore the items that were rewritten. 

```shell
outputs:
  home: [HTML, RSS, JSON, WebAppManifest, headers, redirects]
```

Now type <span style="color:DimGray;background-color: #F0FFFF">hugo server</span> from the website home directory and it should successfully start a server.


```python

```
