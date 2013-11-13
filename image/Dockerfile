# DOCKER-VERSION 0.6.4

FROM phusion/passenger-minimal:0.9.2

MAINTAINER Sam Saffron "https://twitter.com/samsaffron"

RUN apt-get -y update &&\
    apt-get -y install python-software-properties &&\
    add-apt-repository -y ppa:pitti/postgresql &&\
    apt-get -y update &&\
    /build/redis.sh &&\
    rm -f /etc/service/nginx/down &&\
    rm -f /etc/service/redis/down &&\
    /build/ruby2.0.sh &&\
    apt-get install -y build-essential git curl libxml2-dev \
                    libxslt-dev libcurl4-openssl-dev \
                    libssl-dev libyaml-dev libtool \
                    libxslt-dev libxml2-dev gawk curl \
                    pngcrush imagemagick \
                    postgresql-9.2 postgresql-client-9.2 \
                    postgresql-contrib-9.2 libpq-dev libreadline-dev \
                    wget sudo &&\
    apt-get install -y haproxy &&\
    useradd discourse &&\
    mkdir /var/www &&\
    cd /var/www &&\
    git clone https://github.com/discourse/discourse.git &&\
    chown -R discourse /var/www/discourse &&\
    cd /var/www/discourse &&\
    sudo -u discourse RAILS4=1 bundle install --deployment

# RUN cd /var/www/discourse && bundle exec rake db:test:prepare && bundle exec rspec

# mkdir -p /src/godeb && cd /src/godeb && curl -O https://godeb.s3.amazonaws.com/godeb-amd64.tar.gz &&\
# cd /src/godeb && tar -xzvf godeb-amd64.tar.gz &&\
# cd /src/godeb && ./godeb install &&\
# cd /src &&  git clone https://github.com/coreos/etcd.git &&\
# cd /src/etcd && ./build &&\
# cp /src/etcd/etcd /usr/local/bin &&\
