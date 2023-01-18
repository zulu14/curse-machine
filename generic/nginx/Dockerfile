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

RUN	apt install -y lsb-release apt-transport-https ca-certificates wget
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" |tee /etc/apt/sources.list.d/php.list
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get -y install git wget curl tar zip unzip nginx php8.1 php8.1-bcmath php8.1-bz2 php8.1-calendar php8.1-cgi php8.1-common php8.1-ctype php8.1-curl php8.1-dba php8.1-dev php8.1-dom php8.1-embed php8.1-enchant php8.1-exif php8.1-ffi php8.1-fileinfo php8.1-fpm php8.1-ftp php8.1-gd php8.1-gettext php8.1-gmp php8.1-iconv php8.1-imap php8.1-intl php8.1-ldap php8.1-mbstring php8.1-mysqli php8.1-mysqlnd php8.1-odbc php8.1-opcache php8.1-pdo  php8.1-pgsql php8.1-phar php8.1-phpdbg php8.1-posix php8.1-pspell php8.1-shmop php8.1-simplexml php8.1-snmp php8.1-soap php8.1-sockets php8.1-sqlite3 php8.1-sysvmsg php8.1-sysvsem php8.1-sysvshm php8.1-tidy php8.1-tokenizer php8.1-xml php8.1-xmlreader php8.1-xmlwriter php8.1-xsl php8.1-zip && adduser -D -h /home/container container




USER		container
ENV			USER=container HOME=/home/container DEBIAN_FRONTEND=noninteractive
WORKDIR		/home/container

COPY		./entrypoint.sh /entrypoint.sh
CMD		[ "/bin/bash", "/entrypoint.sh" ]
