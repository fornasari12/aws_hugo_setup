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


