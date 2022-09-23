# 部署

## 1. 在github中新建一个respository

![image-20220917161602261](how_to_deploy_a_blog.assets/image-20220917161602261-1663405549250-1.png)

![image-20220917161955923](how_to_deploy_a_blog.assets/image-20220917161955923-1663405549251-3.png)

## 2. 生成并设置SSH

- 在cmd.exe中键入以下内容并一路回车(生成ssh的地址默认即可)

```shell
ssh-keygen -t rsa -C "email_address"
```

![image-20220917162343451](how_to_deploy_a_blog.assets/image-20220917162343451-1663405549250-2.png)

![image-20220917162812408](how_to_deploy_a_blog.assets/image-20220917162812408-1663405549251-4.png)

- 回到github中找到Settings

![image-20220917162907539](how_to_deploy_a_blog.assets/image-20220917162907539-1663405549251-5.png)

![image-20220917161357655](how_to_deploy_a_blog.assets/image-20220917161357655-1663405549251-6.png)

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDXQaylYURPtwwVD8Et2mhPFNa4FksFn/sgsfvJ3E5Re1cRzjqjRhbGB/5LsymbwAnZ3sTrSrj/BrXNsH3U9uhnmC6jlFCVkZHUd99Gg6NShuw34NBHfNubE1P+8Dhs+f6FPWEAxTNhJOBjQ+h2Kd8kZN+KZZqkNSdUBweHv3k9jog1fJXuIeXh7DG9yQrwzZiJJO2pJiMioqEgNcFaNeN4aJO3bNNx0loNqHVL6X/Jkb8yJHRRer69iEJ5DquamTVg1YK/XdqCspLE6gJZcTrDmJqKOnjRoeGeotL1ZNwZGfGAwHHdxpoBTO2ys09Q++NYOgvgILDdSNrdPPBtGs5Aio3vXh20ZpuyIGTU/9yIp4qNh/xgjtW3OogsgXPmvsob4kPW7RKFZ+pnoqM89RYOSibbhNV78Gi6ioubb+kVa/DmaghoY8T4hVFNhBihm7wG4Mr7q35CrqnyanZk6cDydMVh+2H+83kWqsTm+A2OJzp2fRgO8zfRlhoZsuOdjjM= kelin@stu.ecnu.edu.cn