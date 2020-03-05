# Git Settings

Content

- Cache password

### Cache password

```shell
$ git config credential.helper 'cache --timeout=300' # cache 5 min
```

If you would like the daemon to exit early, forgetting all cached credentials before their timeout, you can issue an `exit` action:

```shell
$ git credential-cache exit
```

References:

- [git credential cache](https://git-scm.com/docs/git-credential-cache)