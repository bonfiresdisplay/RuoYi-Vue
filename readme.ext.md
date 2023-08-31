# 备忘录

## 环境
前端
```
> node -v
v18.17.1

> npm -v
9.8.1
```

java
```
> java -version
java version "1.8.0_201"
Java(TM) SE Runtime Environment (build 1.8.0_201-b09)
Java HotSpot(TM) 64-Bit Server VM (build 25.201-b09, mixed mode)
```

mysql
```
> select @@version
5.7.24
```

redis
```
> info server
"# Server
redis_version:6.2.1
redis_git_sha1:00000000
redis_git_dirty:0
redis_build_id:ba735e0ff5068e47
redis_mode:standalone
os:Linux 3.10.0-1160.66.1.el7.x86_64 x86_64
arch_bits:64
multiplexing_api:epoll
atomicvar_api:atomic-builtin
gcc_version:4.8.5
process_id:1067
process_supervised:no
run_id:bd7d0d6fe38281da985b1e567067e17f01fe002d
tcp_port:6379
server_time_usec:1693463385307628
uptime_in_seconds:278057
uptime_in_days:3
hz:10
configured_hz:10
lru_clock:15741785
executable:/usr/local/bin/redis-server
config_file:/etc/redis/6379.conf
io_threads_active:0
"
```


## 后端
1. 修改db、redis配置
   ```
   ruoyi-admin/src/main/resources/application.yml(Line.73)
   ruoyi-admin/src/main/resources/application-druid.yml(Line.9)
   ```
2. 导入sql到相应的mysql库中
   ```
   sql/quartz.sql
   sql/ry_20230706.sql
   ```
3. 启动服务
   ```
   ruoyi-admin/src/main/java/com/ruoyi/RuoYiApplication.java
   ```

## 前端
```
> cd ./ruoyi-ui

# 安装依赖
> npm install --registry=https://registry.npmmirror.com

# 启动服务
> npm run dev

# 构建测试环境
> npm run build:stage

# 构建生产环境
> npm run build:prod

```

因为 npm 版本过高的原因，需要修改启动配置ruoyi-ui/package.json
```
{
  "scripts":{
    "dev": "set NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service serve",
    "build:prod": "set NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service build",
    "build:stage": "set NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service build --mode staging",
    "preview": "set NODE_OPTIONS=--openssl-legacy-provider && node build/index.js --preview",
  }
}
```
报错输出如下:
```
INFO  Starting development server...
10% building 2/5 modules 3 active ...dules\@vue\cli-plugin-eslint\node_modules\eslint-loader\index.js??ref--13-0!D:\p0\RuoYi-Vue\ruoyi-ui\src\main.js E
rror: error:0308010C:digital envelope routines::unsupported
    at new Hash (node:internal/crypto/hash:69:19)
    at Object.createHash (node:crypto:133:10)
    at module.exports (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\util\createHash.js:135:53)
    at NormalModule._initBuildHash (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:417:16)
    at handleParseError (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:471:10)
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:503:5
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:358:12
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:373:3
    at iterateNormalLoaders (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:214:10)
    at iterateNormalLoaders (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:221:10)
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:236:3
    at runSyncOrAsync (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:130:11)
    at iterateNormalLoaders (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:232:2)
    at Array.<anonymous> (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:205:4)
    at Storage.finished (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\enhanced-resolve\lib\CachedInputFileSystem.js:55:16)
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\enhanced-resolve\lib\CachedInputFileSystem.js:91:9
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\graceful-fs\graceful-fs.js:123:16
    at FSReqCallback.readFileAfterClose [as oncomplete] (node:internal/fs/read_file_context:68:3)
node:internal/crypto/hash:69
  this[kHandle] = new _Hash(algorithm, xofLen);
                  ^

Error: error:0308010C:digital envelope routines::unsupported
    at new Hash (node:internal/crypto/hash:69:19)
    at Object.createHash (node:crypto:133:10)
    at module.exports (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\util\createHash.js:135:53)
    at NormalModule._initBuildHash (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:417:16)
    at handleParseError (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:471:10)
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:503:5
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\webpack\lib\NormalModule.js:358:12
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:373:3
    at iterateNormalLoaders (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:214:10)
    at Array.<anonymous> (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\loader-runner\lib\LoaderRunner.js:205:4)
    at Storage.finished (D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\enhanced-resolve\lib\CachedInputFileSystem.js:55:16)
    at D:\p0\RuoYi-Vue\ruoyi-ui\node_modules\graceful-fs\graceful-fs.js:123:16
    at FSReqCallback.readFileAfterClose [as oncomplete] (node:internal/fs/read_file_context:68:3) {
  opensslErrorStack: [ 'error:03000086:digital envelope routines::initialization error' ],
  library: 'digital envelope routines',
  reason: 'unsupported',
  code: 'ERR_OSSL_EVP_UNSUPPORTED'
}
```


## 启动后
1. 默认两个帐号admin/admin123,ry
2. 修改默认密码


## 约定
1. 单独出自有的后台工程game4dream-admin，修改ruoyi-admin的打包pom.xml，避免g4da包体翻倍
2. 不修改ruoyi本身自有的代码，如需修改，则以重写、ext的方式修改


## 概念
1. 一个公司 -> 一个产品 -> 一个后台
2. 一个产品 -> 多发行/代理商(Agency) 例：37，腾讯，自研自发等。指产品推广发行团队
3. 一个产品 -> 多地区(Area) 例：中国、东南亚、美洲、欧洲等。指地理位置、地区
4. 一个产品 -> 多平台/环境(Environment) 例：iOS、安卓、微信小游戏、PC、XBox、H5。指App所在系统平台
5. 一个产品 -> 多游戏(Game) 例：37-中国-iOS，腾讯-美洲-安卓。指一个游戏服列表
6. 一个游戏 -> 多个包(Package) 例：腾讯-美洲-安卓-独代、腾讯-美洲-安卓-华为。 

``` 
例：
37发行，港台地区，安卓/iOS -> Game.1
37发行，港台地区，安卓 -> 一个Package -> Game.1
37发行，港台地区，iOS -> 一个Package -> Game.1
```

自研自发时，为了细化导师效果，要区分导量来源渠道，客户端的一个标识位，给数据分析用
1. 一个产品 -> 多渠道(Channel) 例：独代、AppStore、小米、华为、雷电等。自研自发时使用，独代时只有一个。指不同的App商店，导量渠道

## 服群、服组、节点、逻辑服、游戏服概念
1. 一个服群 -> 一个主服集群(一张服列表，及Server列表) -> 多个服组(Group)
3. 一个服组(Group) -> 多台虚拟机(VirtualMachine)
4. 一台虚拟机 -> 多个节点进程(Process) 不同Group的
5. 一个节点 -> 多个逻辑服(Zone)
6. 一个逻辑服 -> 多个游戏服(Server)


