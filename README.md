# dockercase

Ps: Useful dockerHub starter-images to test before we get started:

- https://hub.docker.com/r/docker/whalesay
- https://hub.docker.com/_/node
- https://hub.docker.com/_/mongo

## To get started, follow this [guide](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/#creating-a-dockerfile)

```
⋊> ~/C/dockercase on master ◦ npm init -y
⋊> ~/C/dockercase on master ◦ npm install
⋊> ~/C/dockercase on master ◦ nano server.js

~/C/dockercase on master ◦ docker build -t username/node-web-app .
Sending build context to Docker daemon 81.41kB
........
Step 1/7
Step 2/7
Step 3/7
Step 4/7
Step 5/7
Step 6/7
Step 7/7
........
Successfully built e2d5be338840a4aa1
Successfully tagged username/node-web-app:latest

⋊> ~/C/dockercase on master ◦ docker images

⋊> ~/C/dockercase on master ◦ docker images 15:40:49
REPOSITORY TAG IMAGE ID CREATED SIZE
username/node-web-app latest e2d5be338840a4aa1 25 seconds ago 920MB
```

## Expose my container on i.e. port: 49160

```
⋊> ~/C/dockercase on master ◦ docker run -p 49160:8080 -d username/node-web-app 15:41:22
1043cd943e0803ebda36d60c70614548584f9632eb5298e205734ff

⋊> ~/C/dockercase on master ◦ docker ps 15:41:46
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
104456d97y989 username/node-web-app "docker-entrypoint.s…" 14 seconds ago Up 13 seconds 0.0.0.0:49160->8080/tcp stupefied_jepsen
....
....
....
⋊> ~/C/dockercase on master ◦
```

## Expose my container on i.e. port: 3009

```
⋊> ~/C/dockercase on master ◦ docker run -p 3009:8080 -ti username/node-web-app 15:50:57
Running on http://0.0.0.0:8080
⋊> ~/C/dockercase on master ◦ curl -i localhost:3009 15:52:29
HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: text/html; charset=utf-8
Content-Length: 11
ETag: W/"b-CkytvgsvknskGd45QIvq3AZd8XYQLvEhtA"
Date: Mon, 28 Sep 2020 13:52:33 GMT
Connection: keep-alive

⋊> ~/C/dockercase on master ◦ curl https://localhost:3009 15:52:33
curl: (35) error:1400410B:SSL routines:CONNECT_CR_SRVR_HELLO:wrong version number
⋊> ~/C/dockercase on master ◦ curl http://localhost:3009 15:54:02
Hello World ⏎

⋊> ~/C/dockercase on master ◦ docker inspect 104456d97y989 ⋊> ~/C/dockercase on master ◦ docker inspect 104456d97y989 15:54:59
[
{
"Id": "1043cd943e0803ebda36d60c70614548584f9632eb5298e205734ff",
"Created": "2020-09-28T13:41:33.3639651Z",
"Path": "docker-entrypoint.sh",
"Args": [
"node",
"server.js"
],
....
....
....
....
"DriverOpts": null
}
}
}
}
]

⋊> ~/C/dockercase on master ◦ curl http://localhost:3009 09:42:39
Hello World⏎

```

## Further Reading:

- https://docker-curriculum.com/
- https://kubernetes.io/docs/tutorials/kubernetes-basics/
- https://www.digitalocean.com/community/tutorials/containerizing-a-node-js-application-for-development-with-docker-compose
- https://www.digitalocean.com/community/tutorials/how-to-build-a-node-js-application-with-docker
