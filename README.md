# psjmxbeat

1. Download a copy of the `JVM-Agent` variant of Jolokia from
https://jolokia.org/download.html and place it on your app/prcs server. Note
the full path.

2. Copy the `jolokia-access.xml` policy file to your app/prcs server and modify
as necessary.

3. Choose a port number, and modify `psappsrv.cfg` or `psprcs.cfg` as shown:
```
[PSMONITORSRV]
JavaVM Options=-Dxdo.ConfigFile=%PS_HOME%/appserv/xdo.cfg -javaagent:/home/psadm2/jolokia-jvm-1.6.1-agent.jar=port=7777,host=localhost,policyLocation=file:///home/psadm2/jolokia-access.xml -Xms32m -Xmx256m
```

4. Install Metricbeat and copy `jolokia-app.yml` or `jolokia-prcs.yml` to the
`modules.d` directory

5. Configure Elastic output options in `metricbeat.yml`

6. Start Metricbeat
