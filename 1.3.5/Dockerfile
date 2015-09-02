FROM artburkart/nginx-php-fpm-phalcon:1.3.5
MAINTAINER Arthur Burkart <artburkart@gmail.com>

# Install V8
RUN apt-get update && apt-get install -y \
  curl subversion build-essential python-dev libreadline-dev git autoconf && \
  svn checkout http://v8.googlecode.com/svn/trunk/ /v8 && \
  cd /v8 && \
  sed -i 's/svn checkout --force/svn checkout --non-interactive --trust-server-cert --force/g' Makefile && \
  make builddeps && \
  make native library=shared -j8 && \
  mkdir -p /usr/local/v8/lib && \
  cp out/native/lib.target/lib*.so /usr/local/v8/lib && \
  echo "create /usr/local/v8/lib/libv8_libplatform.a\naddlib out/native/obj.target/tools/gyp/libv8_libplatform.a\nsave\nend" | ar -M && \
  cp -R include /usr/local/v8 && \
  make clean && \
  cd / && rm -rf /v8 && \
  git clone https://github.com/preillyme/v8js.git /usr/local/src/v8js && \
  cd /usr/local/src/v8js && phpize && ./configure --with-v8js=/usr/local/v8 && \
  cd /usr/local/src/v8js && make all test install && \
  apt-get remove --purge -y subversion build-essential python-dev libreadline-dev autoconf && \
  apt-get autoremove -y && \
  apt-get clean && \
  apt-get autoclean && \
  echo -n > /var/lib/apt/extended_states && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /usr/share/man/?? && \
  rm -rf /usr/share/man/??_* && \
  cd / && rm -rf /v8js && \
  echo "extension=v8js.so" > /etc/php5/fpm/conf.d/23-v8js.ini && \
  echo "extension=v8js.so" > /etc/php5/cli/conf.d/23-v8js.ini
