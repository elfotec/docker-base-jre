# docker-base-jre

Imagem JRE base para os projetos Java 11.

## Monoarch

Only for development...

1. Build

```shell
docker build --compress --tag elfotec/docker-base-jre:11-jre-focal eclipse-temurin-11-jre-focal
```

2. Deploy

```shell
docker login -u elfotec
docker push elfotec/docker-base-jre:11-jre-focal
```

## Multiarch

For production, build a multiarch image.

0. Login

```shell
docker login -u elfotec
```

1. Create builderx

Only for the first time...

```shell
docker buildx create --name elfo-builder --use
```

2. Build and push

```shell
docker buildx use elfo-builder

docker buildx build --platform linux/amd64,linux/arm64 -f eclipse-temurin-11-jre-focal/Dockerfile -t elfotec/docker-base-jre:11-jre-focal --push .

docker buildx imagetools inspect elfotec/docker-base-jre:11-jre-focal
```