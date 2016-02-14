# update package version

To update your nodejs package version, you can either change manually in package.json then commiting,
or use `npm version`. The advantage of using `npm version` is, it also automatically commit the change and
tag it.

- Update major (from 1.0.0 to 2.0.0)

```sh
$ npm version major
```

- Update minor (from 1.0.0 to 1.1.0)

```sh
$ npm version minor
```

- Update patch (from 1.0.0 to 1.0.1)

```sh
$ npm version patch
```

- Pre release

```sh
# from 1.0.0 to 2.0.0-0
$ npm version premajor
# from 1.0.0 to 1.1.0-0
$ npm version preminor
# from 1.0.0 to 1.0.1-0
$ npm version prepatch
```

- Specify your own version (I use this to tag beta release)

```sh
$ npm version 1.0.0-beta.2
```

- Push version tag created by npm version

```sh
$ git push origin master --follow-tags
```
