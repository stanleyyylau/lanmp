## 11.32 php扩展模块安装

**大致流程**

* 下载编译安装redis成redis.so文件（用phpize生成一个configure文件就行了）
* 确保redis.so在PHP动态模块目录下
* 编辑PHP配置文件确保它加载了redis这个模块


```
/usr/local/php/bin/php -m //查看模块
下面安装一个redis的模块
cd /usr/local/src/
wget https://codeload.github.com/phpredis/phpredis/zip/develop 
mv develop phpredis-develop.zip
unzip phpredis-develop.zip
cd phpredis-develop
/usr/local/php/bin/phpize //生成configure文件,然后就可以写编译时候的参数了
./configure --with-php-config=/usr/local/php/bin/php-config
make && make install
/usr/local/php/bin/php -i |grep extension_dir //查看扩展模块存放目录，我们可以在php.ini中去自定义该路径 
```

```
vim /usr/local/php/etc/php.ini  //增加一行配置（可以放到文件最后一行）
extension = redis.so  
```

如果你要编译的扩展模块在PHP源码包里面有，可以直接在里面编译，不用再下载了