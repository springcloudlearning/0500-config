In distribution system. Config component consist of two parts
1)Config Server
2)Config Client

Topology

Eureka(8761)                 -     Service-User(8762)
Config-server(8764)         <--          <-|
Call github

This is a very simple Config server case. and this config-server even didn't register into Eureka server. 
so all config client simply register to one hard code config server path

next chapter will demonstate how to build the HA config server.(will register config server to eureka server)

Resources how to map to 
http://localhost:8764/democonfigclient.message/dev

resources
URL:
https://github.com/springcloudlearning/SpringcloudConfig/blob/master/respo/config-client-dev.properties
File Content:
foo=foo version 2
democonfigclient.message=hello spring io

http request url and resource file mapping as below:(using label when we need to map to specific branch)
/{application}/{profile}[/{label}]
/{application}-{profile}.yml
/{label}/{application}-{profile}.yml
/{application}-{profile}.properties
/{label}/{application}-{profile}.properties

github resource = client properties 
application = spring.application.name = config-client



Config client application need to use bootstrap.properties file instead of application.yml file 
spring.application.name=config-client
spring.cloud.config.label=master
spring.cloud.config.profile=dev
spring.cloud.config.uri=http://localhost:8764/    <-- config-server path

