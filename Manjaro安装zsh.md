
# 1. 安装zsh
```
sudo pacman -S zsh zsh-doc
```
其中，zsh-doc安装在/usr/share/doc/zsh/文件夹下，包含html和pdf格式的zsh文档。
# 2. 安装manjaro主题
```
sudo pacman -S manjaro-zsh-config #manjaro的zsh配置文档。
```
# 3. 复制配置文件
```
cp /etc/skel/.zshrc ~/.zshrc #将配置文件复制到用户目录
```
更新版本后也需要重新复制这个配置文件，以便
