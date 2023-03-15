# jboss-eap7-domains-labs
JBoss EAP 7 Domain deployments – Part 1: Setup a simple EAP Domain
This repository is used to track all the configuration changed in the JBoss EAP 7 Labs.

1 Domain Controller on a machine called host0.

1 Host Controller on a machine host1 with two EAP instances Server11 and Server12

1 Host Controller on a machine host2 with Three EAP Instances Servers21, Server22 and  Server23

Host0 should be run as the master controller

Host1 and Host2 are slaves connecting to Host0

  Server11 and Server21 are members of the primary server group ( name=primary-server-group)
  
  Server12 and Server22 belong  to the secondary server group (name=secondary-server-group)
  
  Server23 is the only member of the  singleton server group ( name= singleton-server-group)
  
In real life Machine Host1, Host2 are mostly  in different physical location but for the purpose of this tutorial we are going to simulate them  on the same localhost using a signed EAP 6.4 installation and different configuration folders for each Machine.

## Start the domain controller

```
>D:\JBOSS\DOMAIN\labs\wildfly-21.0.2.Final\bin\domain.bat --host-config=host-master.xml -Djboss.domain.base.dir=D:\JBOSS\DOMAIN\labs\host0\domain
```

By default the domain.sh script start with file host.xml, so we have to use the option  --host-config to point on host-master.xml,

Second we have to specify the boss base dir for host0: host0/domain

Now we can connect on the domain using http://localhost:9990  using the admin/Admin01# user and browse the domain configuration. You can see the host0-master and the different server groups we added in domain.xml. All these configurations can be done on the management console

##  Start  Host Controller 1

```

D:\JBOSS\DOMAIN\labs\wildfly-21.0.2.Final\bin\domain.bat --host-config=host-slave.xml -Djboss.domain.base.dir=D:\JBOSS\DOMAIN\labs\host1\domain
```

##  Start  Host Controller 2

```
D:\JBOSS\DOMAIN\labs\wildfly-21.0.2.Final\bin\domain.bat --host-config=host-slave.xml
-Djboss.domain.base.dir=D:\JBOSS\DOMAIN\labs\host2\domain
```
