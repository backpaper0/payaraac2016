これは[Payara Advent Calendar 2016](http://qiita.com/advent-calendar/2016/payara)の19日目です。

PayaraにはDockerイメージが用意されており、Docker Hubで公開されています。

* https://hub.docker.com/u/payara/

この中から、Payara Microのイメージを使ってアプリケーションを動かすコマンドは次のようになります。

```console
docker run -d --name=helloworld -p 8080:8080 \
           -v `pwd`/helloworld/build/libs:/opt/payara/deployments:ro \
           payara/micro java -jar /opt/payara/payara-micro.jar \
           --deploy /opt/payara/deployments/helloworld.war
```

`-p`で8080ポートへアクセスできるようにしています。
`-v`でWARファイルが格納されているディレクトリ（上記では`build/libs`）を`/opt/payara/deployments`にマウントしています。
あとはイメージ（`payara/micro`）を指定して、Payara Microを動かすための`java`コマンドを書いています。

以上のように、ただでさえJAR一つで楽に動かせるPayara Microを、Dockerを使ってもっと楽に動かしてみました（JARを取ってくる必要がないので、個人的にはより楽になっています）。
Docker Hubには`payara/server-full`や`payara/server-web`、それから`payara/microprofile`もあるので、これらを使ってもう少し遊んでみようと思います。

Docker上のPayara Microを試すために作ったHello worldするだけのアプリをGitHubに置いてるので良かったら試してみてください。

* https://github.com/backpaper0/payaraac2016

以上⛄️
