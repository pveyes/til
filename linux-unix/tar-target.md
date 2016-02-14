# tar target

When you use `tar`, you can specify the source(s) (if you compress) or destination (if you extract)

- Add multiple files to archive

```sh
$ tar -czf bundle.tar.gz README.md package.json src
```

- Extract archive to specific directory

```sh
$ tar -xzf bundle.tar.gz -C /path/to/output/directory
```
