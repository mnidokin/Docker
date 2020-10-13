FROM ruby

MAINTAINER mnidokin <mnidokin@student.21-school.ru>

RUN apt-get update  && \
	apt-get upgrade -y && \
	apt-get install build-essential nodejs sqlite3 -y

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed
