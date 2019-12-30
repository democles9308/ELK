# ELK
My ELK-stack related files

Based on the work of a3ilson(https://github.com/a3ilson/pfelk), created my own set of files and use the on my OPNSense / Pfsense setups.
My Els-stack is running in different docker-containers. I use the commands below to create them... I'd better create
a docker-compose file for this but this works  ;-)

docker run -d -it -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -h elasticsearch --name elasticsearch --mount source=ES-data,target=/usr/share/elasticsearch/data elasticsearch:7.5.1
docker run -d -it -p 5044:5044 -p 9600:9600 -p 5140:5140/udp -h logstash --name logstash -v /opt/logstash/pipeline:/usr/share/logstash/pipeline -v /opt/logstash/patterns:/etc/logstash/patterns -v /opt/logstash:/etc/logstash -v /opt/logstash/geoip:/usr/share/GeoIP --link elasticsearch:elasticsearch logstash:7.5.1
docker run -d -it -p 5601:5601 -h kibana --name kibana --link elasticsearch:elasticsearch kibana:7.5.1

For the dasboards and graphs, I'll add interesting topics/files here as well as a kind of 'memory'

