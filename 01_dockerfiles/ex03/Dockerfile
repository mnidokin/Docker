FROM debian

MAINTAINER mnidokin <mnidokin@student.21-school.ru>

ENV TERM xterm

RUN apt-get update && \
    apt-get install -y xterm curl openssh-server ca-certificates postfix tzdata

RUN curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash && \
	EXTERNAL_URL="http://192.168.99.111:8080" && \
	apt-get install -y gitlab-ce
			    
RUN sed -i "s/# grafana\['enable'\] = true/grafana['enable'] = false/g" /etc/gitlab/gitlab.rb && \
	sed -i "s/# prometheus_monitoring\['enable'\] = true/prometheus_monitoring\['enable'\] = false/g" /etc/gitlab/gitlab.rb && \
	sed -i "s/# unicorn\['worker_timeout'\] = 60/unicorn\['worker_timeout'\] = 300/g" /etc/gitlab/gitlab.rb

EXPOSE 443 80 22

ENTRYPOINT  (/opt/gitlab/embedded/bin/runsvdir-start &) && \
			gitlab-ctl reconfigure && \
			tail -f /dev/null
