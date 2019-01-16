* Useful configs, usefuls cripts, everything that I'm using:

Spring boot config for develop with H2:

filename: application-dev.properties
# H2
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
# Datasource
spring.datasource.url=jdbc:h2:file:~/test
spring.datasource.username=sa
spring.datasource.password=
spring.datasource.driver-class-name=org.h2.Driver
logging.level.org.hibernate.SQL=DEBUG
logging.level.org.hibernate.type.descriptor.sql.BasicBinder=TRACE

Active spring profile dev (vm argument): -Dspring.profiles.active=test
