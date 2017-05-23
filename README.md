# Docker Ctrip Apollo.
使用 Docker 部署携程 Apollo，为提高扩展性拆为 3 个 Docker Image。

#### 部署说明：

1. 修改官方项目 apollo-configservice 、apollo-adminservice 项目下 application.yml 配置文件，此处可参考[官网文档](https://github.com/ctripcorp/apollo/wiki/分布式部署指南#14网络策略)：

   ```yaml
   spring:
       application:
           name: apollo-configservice
       profiles:
       	active: ${apollo_profile}
       cloud:
           inetutils:
               ignoredInterfaces:
               - docker0
               - veth.*
   ```


2. 按照官方文档配置完成后，执行 ./build.sh 编译打包。

3. 下载并解压本项目到官方项目根目录，分别编译 apollo-configservice 、apollo-adminservice 、apollo-portal，编译及运行说明可参考下方或目录中 Dockerfile 文件。

   ```shell
   # Build with:
   docker build -t apollo-configservice .
   # Run with:
   docker run -p 8080:8080 -d --name apollo-configservice apollo-configservice
   ```

4. 访问 http://IP:PORT 查看部署是否成功。

