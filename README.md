# mllp-http-transformer
An HTTP/MLLP and MLLP/HTTP transformer

This project consists of 1 servlet making it transparent to consumers and senders whether MLLP or HTTP is being used as a transport format for HL7v2 messages. The servlet spawns threads (controlled by the default thread factory of HAPI - so it is not totally havoc) for the MLLP-part when consuming and sending so deploying in a strict servlet container is probably not an option. It can however be used as a proxy in front of whatever services you have in your environment that fit your needs - being HTTP or MLLP - or both. Enjoy!

Default setup is the following:

MLLP-2-HTTP
inbound MLLP port: 2575
outbound URL: http://localhost:8080/http

HTTP-2-MLLP
inbound URL: http://localhost:8080/http
outbound MLLP port: 2576
outbound MLLP host: localhost

Ports, URL's and host is configurable on the web.xml

'Quick-and-dirty' deploy can be done using 'java -jar jetty-runner.jar mllp-http-transformer.war'


PS. On my sloppy machine, 200 'protocol format transformations' can be conducted pr. sec.
