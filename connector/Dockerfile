FROM confluentinc/cp-server-connect-base:7.4.0

# Install the JDBC connector
RUN confluent-hub install --no-prompt confluentinc/kafka-connect-jdbc:10.7.1

RUN wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-8.0.27.tar.gz
RUN tar -xvzf /home/appuser/mysql-connector-java-8.0.27.tar.gz -C /etc/kafka-connect/jars/ --strip-components=1
