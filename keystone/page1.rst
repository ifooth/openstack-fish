===================
KeyStone 菜鸟教程
===================

1 使用memcache代替kvs或者sql

安装memcache服务端
安装memcache客户端 keystone使用的是python-memcached
修改配置文件
driver = keystone.token.backends.memcache.Token

2 怎么查询token

token_id 由下列算法生成
如果token_format 为UUID 则token_id 就是token 的ID
如果token_format 为pki 则token_id 为prefix+md5(token)
prefix= token-
如token-8e6079b739b01432962656c9128748cb

telnet 查询
telnet localhost 11211
get token-8e6079b739b01432962656c9128748cb

python库查询
import memcache
m = memcache.Client(['localhost:11211'])
m.get（'token-8e6079b739b01432962656c9128748cb')