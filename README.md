# Ruby on Rails Restful API template

Rails Restful API backend template - project generator/development environment.
Can be used by Ruby developers for quick start on building Restful API's using Ruby on Rails framework.
This project is aimed to simmplify development environment setup and includes many useful dev tools like RabbitMQ, Redis, Elasticsearch, Kibana, Logstash, Filebeat, DB.

## Stack includes

* RabbitMQ 
* Redis 
* Kibana
* Elasticsearch
* Logstash
* Filebeat
* PostgreSQL
* Nginx
* Supervisord

Ruby libraries included:
* libssl-dev
* libyaml-dev
* libreadline-dev
* zlib1g-dev
* libncurses5-dev
* libffi-dev
* libgdbm-dev
* libgmp-dev

Gems:
* bundler
* rails
* jquery-rails


## Installation
1. Clone this project into your work directory:
```sh
$ git clone "https://github.com/trydirect/ror-restful.git"
```

2. Bring up services with docker-compose:
```sh
$ cd rails-restful/v01/dockerfiles
$ docker-compose up -d
```


3. Let's check running containers

```
$ docker-compose ps
```

```
Name                  Command                          State          Ports
------------------------------------------------------------------------------------------------------------------------------
db                    docker-entrypoint.sh postgres    Up (healthy)   5432/tcp
elasticsearch         /docker-entrypoint.sh elas ...   Up             0.0.0.0:9200->9200/tcp, 0.0.0.0:9300->9300/tcp
kibana                /docker-entrypoint.sh kibana     Up             0.0.0.0:5601->5601/tcp
logstash              /docker-entrypoint.sh -e         Up             0.0.0.0:5044->5044/tcp, 9600/tcp
filebeat              /usr/local/bin/docker ...        Up
mq                    docker-entrypoint.sh rabbi ...   Up (healthy)   15671/tcp, 0.0.0.0:21072->15672/tcp, 25672/tcp, 4369/tcp, 5671/tcp, 0.0.0.0:2172->5672/tcp,0.0.0.0:32770->5672/tcp
nginx                 /usr/bin/supervisord -c /e ...   Up             0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
redis                 docker-entrypoint.sh redis ...   Up (healthy)   6379/tcp
web                   /usr/bin/supervisord -c /e ...   Up             0.0.0.0:8000->8000/tcp   
```

4. Run tests

```
$ python ../../tests.py
```

## Contributing

1. Fork it (https://github.com/trydirect/ror-restful/fork)
2. Create your feature branch (git checkout -b feature/fooBar)
3. Commit your changes (git commit -am 'Add some fooBar')
4. Push to the branch (git push origin feature/fooBar)
5. Create a new Pull Request
