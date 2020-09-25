---
layout: post
title:  "K8S-Jenkins-ʹ��ָ��"
date:   2020-09-25 15:35:18 +0800
categories: dev
---

## ָ�ϼ��
��������򵥽���һ������֮ǰ���õĹ�������ģʽ��Jenkins ��������Mac��+ �ڵ������Linux��Windows��Mac�����漰��������Ŀ����Java��.Net��IOS��Andriod�Լ�΢��С���򣬹����ű�������Jenkinsfile�б�дPipelines������洢
����Git���й���ÿһ����Ŀ��Git�ֿ��¶������Jenkinsfile����������ȫ�̵ļ����׶Σ��Լ�Jenkins-project.json���ļ����Լ���ģ����������׶��ǵľ���ʵ�֣���������ʼʱ���û�ѡ��ڵ��������Jenkins master����������䣬
�ڵ�ɲ����ɴ��н��д������ʵ�ֲ��衣

������ǹ����Ͳ���ķ�ʽ��ԭ����ȣ��Ѿ�����ͬ�����ȣ�Java��Ŀ������war�ļ������ھ���Ľڵ������ʵ���������������Ͻ��й��������ǲ���Docker��pod�����������������������л��գ�������Ŀ���ɲ��ýڵ��������ģʽ��
��Σ������ű�ģʽҲ�����˸ı䣬���ڱ�д�߶��ԣ������ϲ�����Ҫ����Pipelines�﷨֪ʶ��Ϊǰ�ᣬ���ǿ���ͨ������json����yaml�ļ��Ϳ���ʵ�ֹ����ľ��岽�裬����ο�
* [jenkins-json-build](http://git.gyyx.cn/lib/cn-gyyx-jenkins-libraries.git)����������������й���������ʹ�õ�����CI\CD���̡�

## �漰ϵͳ������

### Jenkins
1. �����û������û�ע�ᡢ�οͲ��ɷ��ʡ������û�Ȩ�ޣ����ð�ȫ���󣩣�
2. ����ϵͳ���ã���������ַ�������ᵽ��jenkins-json-build���������ʼ�֪ͨ����ϵͳ����-ϵͳ����-ϵͳ����Ա�ʼ���ַ ����д���ʼ���ַ������Ƿ����ˣ���ϵͳ����-ϵͳ����-Extended E-mail Notification-SMTP server ����д�������������ַ����ϵͳ����-ϵͳ����-Extended E-mail Notification-�߼� ����Use SMTP Authentication����д��������������룬ע��������� һ���ú�ϵͳ����Ա�ʼ���ַ�ʼ���ַ��ͬ���мǣ���
3. ��Ҫ�漰�Ĳ����װ��Kubernetes��Git��أ�Git��Git Parameter����Pipeline��ء�SSH��أ�
4. ��ͼ������ͬһ��Ŀ�ĸ�������������ͬһ��ͼ�£�
5. �ڵ������Ҫʹ�õ��Ļ���ͨ��Launch agents via SSH�������ӣ�

### ����ϵͳ
�����ڲ�������һ��ϵͳ�����������¼���
1. �ṩ�ⲿ�ӿڣ�ʵ��ΪJenkins��ΪDockfile���ǩ�׶�ʱ�ṩ�°汾�ţ�ĿǰΪ4λ��0.0.0.0����1λ����Ŀ�汾����2λ�ǵ����汾����3λ�ǲ��𻷾�����4λ�ǲ���ԭ�򣩣�ǰ������Ҫ�ڲ���ϵͳ�н�����ص����ã��ο���ͼ��
2. ����ñ�ǩ��Dockerfile push�������������Լ����п粿�ŵĵ��ýӿڣ�


## �����ľ���ʵ��

### ����ͼ����
![Docker��Ŀ](/static/2020-09/Dockerbuild.png)

### ��ͬһ�ֿ��°������վ��ʱ��ʵ�ַ�ʽ������ͬ��
��Ŀ��Ŀ¼�µ�Jenkinsfile��Ҫ����projectlist��ʵ���ڹ���ʱѡ���ĸ�վ����й������ļ��������£�
![Jenkinsfile](/static/2020-09/Jenkinsfile.png)
project-list.yaml��key��value�ֱ��Ӧ��������ѡ�����ʾ���ʵ��ֵ���ο���ͼ��������value��ֵ��Ϊ�ֿ��Ŀ¼�µ���Ŀ¼�㼶���ļ������ƣ���������Ŀ¼��Ҫ����jenkins-project.json�ļ���ÿһ����Ҫ������վ��Ŀ¼����
json�ļ������໥�����ģ��ɸ��Ի����ã���Ҳ�Ǻ�֮ǰ�Ĺ�����ʽ��ͬ��һ���ط���֮ǰ���ǲֿ��½�����һ��jenkins-project.json�ļ���������Ҫ������վ��Ĳ��𷽰�ͨͨд�����棬���Ҿ�����������2�֣����������Ͳ���������
�ļ��������ظ����׻���
![project-list](/static/2020-09/project-list.png)
���棬���ĳһ��վ���jenkins-project.json�����ļ�����˵����  
1. �ļ�ȫ���﷨��Ҫ����json��key-value��ʽ������value��Ϊ�ַ������߶���  
2. RuntimeVariable�еı���PROJECT_VERSIONΪ���������ᵽ�Ĳ���ӿڷ���HTTP Get��������ã��õ��Ľ��Ϊ4λ�汾�ţ�������Ҫ��ǰ�ڲ���ϵͳ�ж�${PROJECT_VERSION}����������ã����£�  
   * �����������ַ�������linux���Զ����ļ�·����дϵͳ���ľ���·����  
   * Ϊ��������������Ŀ�����û�У���Ҫ�½���������ɺ󣬼ǵû���Ҫ��������棩��  
   * ��xx.xx.xx.xx��/data/JavaBuild/build Ŀ¼�´���������ͬ�����ļ��У�������Ҫ����һ��ROOT.war����Ϊ�գ�  
   * ��ӷַ���xx.xx.xx.xx����Ҫ���3�����ͣ��ַ������ԡ���ʽ�������в��Ժ���ʽ����Ҫ���� TomcatAppĿ¼ �� Tomcat���ƣ�ֵ�ֱ�Ϊ/data/WEB/����/website/��������  
   * �������ݿ⣬update [dbo].[domain_tb] set is_support_docker = 1 where [domain] = '����';  
3. ���С����𡱼����µĶ����пɰ���������𷽰����������ᵽ�Ĳ������������������ȣ�ÿһ�����𷽰��еĽű�ִ�����ͷ�ΪCOMMAND_STDOUT��COMMAND_STATUS��COMMAND_STATUS_FOR���֣�������Ҫ���ó�
����һ�ּ��ɣ������ж�3�����͵ļ�Ҫ˵������ϸ�ɲο�* [����˵��](https://github.com/sunweisheng/jenkins-json-build#Json%E6%96%87%E6%A1%A3%E6%A0%BC%E5%BC%8F%E5%8F%8A%E8%BF%90%E8%A1%8C%E6%96%B9%E5%BC%8F)  
   * COMMAND_STDOUT��ִ�������нű�������ű��ı�׼������ݣ�  
   * COMMAND_STATUS��ִ�������нű�������ű��ķ���ֵ��0����ɹ�����0����ʧ�ܣ���  
   * COMMAND_STATUS_FOR��ѭ��������Ҫִ�еĽű�Ȼ����COMMAND_STATUS��ʽִ�У�  
4. Script�е������ʽ��Ҫע�������ַ���ת�����⣬������˫������ʹ��˫���ţ�Ӧ����"\\""����ʹ�ö������������ʽ���ɲο������һ�У�  
   * `"docker-tag��֧": "if [ $DEPLOY_BUILD ]; then version=\\"$(curl ${projectoaurl}?user=${Jenkins@BUILD_USER}\\&domainname=${dockerAppName}\\&desc=${dockerImageServer_exter}/baseimages/${dockerImageName}:$version)\\";cd ${ProjectRoot}/${jarFilePath};curl -fL -o ${ProjectRoot}/${jarFilePath}/Dockerfile http://xx.xx.xx.xx/Dockerfile;echo $version;docker build -t ${dockerImageServer_exter}/baseimages/${dockerImageName}:$version .;docker push ${dockerImageServer_exter}/baseimages/${dockerImageName}:$version;rm -rf ${ProjectRoot}/${jarFilePath}/Dockerfile; fi"`

![jenkins-project](/static/2020-09/jenkins-project.png)






