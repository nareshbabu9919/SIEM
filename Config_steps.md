```
sudo vi /etc/rsyslog.conf
```

```
# TAC - catalina.out
input(type="imfile"
      File="/appmnt/Talend-8.0.1/tac/apache-tomcat/logs/catalina.out"
      Tag="TAC"
      Facility="local0")

# TAC - Audit JSON
input(type="imfile"
      File="/appmnt/Talend-8.0.1/tac/audit/tac-audit.json"
      Tag="TAC-AUDIT"
      Facility="local1")

# TDS - Application Log
input(type="imfile"
      File="/appmnt/Talend-8.0.1/tds/tds.log"
      Tag="TDS"
      Facility="local2")

# TDS - Audit JSON
input(type="imfile"
      File="/appmnt/Talend-8.0.1/tds/audit/tds-audit.json"
      Tag="TDS-AUDIT"
      Facility="local3")

# TDP - Application Log
input(type="imfile"
      File="/appmnt/Talend-8.0.1/dataprep/tdp.log"
      Tag="TDP"
      Facility="local4")

# TDP - Audit JSON
input(type="imfile"
      File="/appmnt/Talend-8.0.1/dataprep/audit/tdp-audit.json"
      Tag="TDP-AUDIT"
      Facility="local5")

# TDC - Application Log
input(type="imfile"
      File="/appmnt/TalendDataCatalog/tomcat/logs/catalina.out"
      Tag="TDC"
      Facility="local6")

# Forward all logs to the remote syslog server
*.* @10.3.70.152:514
```



Check the configuration: ``` sudo rsyslogd -N1 ```

Restart the service: ```sudo systemctl restart rsyslog ```

Verify it's running: ```sudo systemctl status rsyslog ```

