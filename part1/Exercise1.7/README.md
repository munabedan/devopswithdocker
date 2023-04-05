## 1.7: Image for script

- Create a new file on your local machine with and append the script we used previously into that file

```shell
$ touch script.sh
$ echo "echo 'Input website:'; read website; echo 'Searching..'; sleep 1; curl http://$website;" > script.sh
```

- Dockerfile

    See file [Dockerfile](Dockerfile)

- Create container

```shell
$ docker build -t curler 
```