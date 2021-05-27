# aws_hugo_setup
Initial Setup of AWS Cloud9 and GitHub for Hugo


1) [Download Hugo](https://github.com/gohugoio/hugo/releases) - hugo_0.83.1_Linux-64bit.tar.gz

```shell
wget https://github.com/gohugoio/hugo/releases/download/v0.83.1/hugo_0.83.1_Linux-64bit.tar.gz
tar zxvf hugo_0.83.1_Linux-64bit.tar.gz

# Create Bin directory adn move to bin
mkdir -p ~/bin
mv hugo ~/bin/

# Check installation
hugo version
```

2) Create Hugo new Site

```shell
hugo new site quickstart
```

3) Move created new site to the github repository folder and all the stuff to the root folder

```
mv quickstart/* $HOME/environment/aws_hugo_setup
```

4) Create giut submodule for the theme to use

```shell
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo 'theme = "ananke"'>>config.toml
```

5) add .gitignore with "public" folder.

6) Create first post and change values

```shell
hugo new posts/my-first-post.md
```
```
---
title: "Dale Putito daleeee"
date: 2021-05-27T21:33:38Z
draft: false
---
```

7) Open por for EC2 instance from aws console, add rule to port 8080 to preview Hugo

![Screen Shot 2021-05-27 at 18 38 09](https://user-images.githubusercontent.com/57304126/119900280-b3b57280-bf1a-11eb-8366-1da87af76d9d.png)

8) Get ip

```shell
curl ipinfo.io

hugo serve --bind=0.0.0.0 --port=8080 --baseURL=http://3.236.40.124/
```

9) Create folders and public folder where all the html will be stored.

```
hugo
```

### Copy Hugo Data into AWS Cloud9 S3 Bucket

1) Create Bucket

![Screen Shot 2021-05-27 at 18 58 23](https://user-images.githubusercontent.com/57304126/119902392-86b68f00-bf1d-11eb-85f5-f5231532423a.png)

Bucket policy: 

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::hellocloud4data1/*"
        }
    ]
}
```
