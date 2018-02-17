### PHP Build From Source
```sh
sudo apt install apache2-dev \ 
		 libxml2-dev \
		 libcurl4-openssl-dev \
		 libjpeg-dev \
		 libpng16-dev \
		 libxmp-dev \
		 libmysqlclient-dev \
		 libpq-dev \
		 libicu-dev \
		 libldap2-dev \
		 libxslt1-dev
		 

./configure \
  --enable-mbstring \
  --with-curl \
  --with-openssl \
  --with-xmlrpc \
  --enable-soap \
  --enable-zip \
  --with-gd \
  --with-jpeg-dir \
  --with-png-dir \
  --with-pgsql \
  --enable-embedded-mysqli \
  --enable-intl \
  --with-xsl \
  --with-pdo-mysql
  
make
  ```
