# 备忘录

### 环境
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


### 后端
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

### 前端
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