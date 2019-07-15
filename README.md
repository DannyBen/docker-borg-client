Borg Backup Client Docker on Alpine
==================================================

[Source code on GitHub][3] | [Image on DockerHub][4]

---

This is a docker image for [borg backup][1] based on Alpine linux.

It is intended to be used as a borg client, and not as a borg server (which
requires a little more setup with sshd).


Quick Start
--------------------------------------------------

Download the files in the [example](example) folder, and then run:

```
$ docker-compose run init
$ docker-compose run backup
$ docker-compose run index
$ docker-compose run list
```


Usage
--------------------------------------------------

```
$ docker run --rm -it \
  -v $PWD/back-me-up:/borg/source \
  -v $PWD/repo:/borg/repo \
  -v cache:/root/.cache/borg \
  -v config:/root/.config/borg \
  -v ssh:/root/.ssh \
  -v $PWD/keys/testkey_id_rsa:/root/.ssh/id_rsa:ro \
  -e BORG_REPO=/borg/repo \
  dannyben/borg-client init -e none
```



[1]: https://borgbackup.readthedocs.io/en/stable/
[2]: https://bugs.alpinelinux.org/issues/10401
[3]: https://github.com/DannyBen/docker-borg-client
[4]: https://hub.docker.com/r/dannyben/borg-client
