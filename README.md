
- [x] install php version 8
- [x] install composer
- [x] install nodeJS version 15.x
- [x] install apache2 (httpd) and config for php-fpm
- [x] install and config oh-my-zsh
- [x] add my favorite alias

### First step
```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository ppa:ondrej/php
$ sudo apt install curl
$ curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -

$ sudo apt update    ;if not update with last command
```

### Install PHP, nodejs, redis, mongodb, apache(httpd), ZSH, tilix and PHP Composer,
```
$ sudo apt install -y git apache2 php8.0 php8.0-fpm libapache2-mod-php8.0 php8.0-mysql libapachip php8.0-curl php8.0-redis e2-mod-fcgid php8.0-mbstring php8.0-dev php8.0-zip php8.0-curl mysql-server make nodejs gcc g++ unzip unrar tilix redis mongodb zsh zsh-theme-powerlevel9k zsh-syntax-highlighting

$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/mohammadghasemi1379/my-ubuntu-config/main/install_composer.sh)"
```

### Enable **php-fpm** for **apache**
```
$ sudo a2enmod proxy_fcgi setenvif
$ sudo a2enconf php8.0-fpm
$ systemctl restart apache2
```

### Change default terminal to **tilix**
```
$ sudo update-alternatives --config x-terminal-emulator
```

### Change bash to zsh
```
$ sudo usermod -s /usr/bin/zsh $(whoami)
```
after this some times need to `reboot`


### First step **git** config
```
$ git config --global user.email "mohamamdgh.dev@gmail.com"
$ git config --global user.name "Mohammad Ghasemi"
```

### Add alias to **~/.zshrc**
```
$ curl https://raw.githubusercontent.com/mohammadghasemi1379/my-ubuntu-config/main/alias >> ~/.zshrc
```

#### Install **phpmyadmin** and **mysql** ALTER USER root WITH native password
```
$ sudo apt install -y phpmyadmin 
$ sudo mysql -u root -p

    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'S3cret_pAsA';
    FLUSH PRIVILEGES;

$ sudo sh -c 'echo Include /etc/phpmyadmin/apache.conf >> /etc/apache2/apache2.conf'
$ sudo service apache2 restart && sudo service mysql restart
```
### Config **OH MY ZSH**
```
$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
$ sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
$ echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
```

* open `~/.zshrc` with `nano ~/.zshrc` comand <br>
    * change oh my zsh theme to `agnoster` <br>
        - find and change `ZSH_THEME="agnoster"` line. <br>
    * and add this plugins `plugins=(git colored-man-pages zsh-autosuggestions sudo command-not-found)`

### Get version of node(& npm) and PHP
```
$ node -v && npm -v && php -v
```

#### Install laravel installer
```
composer global require laravel/installer
```