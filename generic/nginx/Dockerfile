#
# Copyright (c) 2021 Matthew Penner
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

FROM		--platform=$TARGETOS/$TARGETARCH debian:stable-slim

LABEL		author="Matthew Penner" maintainer="matthew@pterodactyl.io"

LABEL		org.opencontainers.image.source="https://github.com/matthewpi/images"
LABEL		org.opencontainers.image.licenses=MIT

RUN apt-get update -y && apt-get upgrade -y
RUN	apt install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2 sudo curl wget
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/sury-php.list
RUN wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -
RUN apt-get update -y
RUN apt-get -y install git wget curl tar zip unzip nginx php8.0 php8.0-bcmath php8.0-bz2 php8.0-calendar php8.0-cgi php8.0-common php8.0-ctype php8.0-curl php8.0-dba php8.0-dev php8.0-dom php8.0-embed php8.0-enchant php8.0-exif php8.0-ffi php8.0-fileinfo php8.0-fpm php8.0-ftp php8.0-gd php8.0-gettext php8.0-gmp php8.0-iconv php8.0-imap php8.0-intl php8.0-ldap php8.0-mbstring php8.0-mysqli php8.0-mysqlnd php8.0-odbc php8.0-opcache php8.0-pdo  php8.0-pgsql php8.0-phar php8.0-phpdbg php8.0-posix php8.0-pspell php8.0-shmop php8.0-simplexml php8.0-snmp php8.0-soap php8.0-sockets php8.0-sqlite3 php8.0-sysvmsg php8.0-sysvsem php8.0-sysvshm php8.0-tidy php8.0-tokenizer php8.0-xml php8.0-xmlreader php8.0-xmlwriter php8.0-xsl php8.0-zip && adduser -D -h /home/container container




USER		container
ENV			USER=container HOME=/home/container DEBIAN_FRONTEND=noninteractive
WORKDIR		/home/container

COPY		./entrypoint.sh /entrypoint.sh
CMD		[ "/bin/bash", "/entrypoint.sh" ]
