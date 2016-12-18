# Hello, world! on Docker payara/micro

[Payara Advent Calendar 2016](http://qiita.com/advent-calendar/2016/payara)

## Prepare

```console
cd helloworld
gradlew build
cd ..
```

## Run

```console
docker run -d --name=helloworld -p 8080:8080 \
           -v `pwd`/helloworld/build/libs:/opt/payara/deployments:ro \
           payara/micro java -jar /opt/payara/payara-micro.jar \
           --deploy /opt/payara/deployments/helloworld.war
```

## License

Licensed under [The MIT License](https://opensource.org/licenses/MIT)
