FROM sebp/elk:512

# overwrite existing file
ADD /conf/nginx.conf /etc/logstash/conf.d/
#ADD /conf/syslog.conf /etc/logstash/conf.d/
ADD /conf/custom-mappings.json /etc/logstash/
ADD /conf/boxes.yaml /etc/logstash/
ADD /conf/applications.yaml /etc/logstash/
ADD /conf/patterns/* ${LOGSTASH_HOME}/patterns/
RUN chown -R logstash:logstash ${LOGSTASH_HOME}/patterns

ADD https://rubygems.org/downloads/logstash-filter-dateparts-2.1.1.gem /

RUN ${LOGSTASH_HOME}/bin/logstash-plugin install --no-verify /logstash-filter-dateparts-2.1.1.gem

RUN ${LOGSTASH_HOME}/bin/logstash-plugin install logstash-filter-translate

RUN ${LOGSTASH_HOME}/bin/logstash-plugin install logstash-filter-aggregate

VOLUME /logs
