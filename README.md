# Cloud Foundry Hello Buildpack

This buildpack does nothing useful: its purpose is to create a single file within
the Droplet filesystem.

Do not use this buildpack alone: you cannot run apps with this buildpack.
You should instead include this buildpack as an addon to your primary buildpack:

```yaml
---
applications:
- name: hellocloudfoundry
  memory: 1G
  random-route: true
  path: app/target/hellocloudfoundry.jar
  buildpacks:
  - https://github.com/alexandreroman/hello-buildpack.git
  - https://github.com/cloudfoundry/java-buildpack.git
```

If you inspect the running app container, you should be able to see a new file
created in `/home/vcap/app`:
```shell
$ cf ssh hellocloudfoundry
vcap@6f652c7f-ad8a-4bd4-55bc-8b27:~$ cat /home/vcap/app/hello.txt
Hello world!
```

Use this buildpack with
[Cloud Foundry Multi Buildpack Demo](https://github.com/alexandreroman/cf-multi-buildpack-demo)
to show the use of multi-buildpack for your apps.

## Contribute

Contributions are always welcome!

Feel free to open issues & send PR.

## License

Copyright &copy; 2018 Pivotal Software, Inc.

This project is licensed under the [Apache Software License version 2.0](https://www.apache.org/licenses/LICENSE-2.0).

