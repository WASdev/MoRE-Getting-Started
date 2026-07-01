# Introduction for IBM Modernized Runtime Extension for Java 

# Introduction

[IBM Modernized Runtime Extension for Java](https://www.ibm.com/docs/en/more) (MoRE) is an extension of WebSphere® Application Server Network Deployment (ND) 9.0.5 that enables you to run and manage Liberty servers from the traditional WebSphere environment. With MoRE, Liberty servers can be configured, clustered, and administered using familiar tools like the administrative console and wsadmin scripting.

## About this lab

In this interactive, hands-on lab, you'll explore the cutting-edge capabilities of WebSphere Application Server and MoRE, which are designed to supercharge your modernization journey. 

Through guided modules, you'll deploy modern Jakarta EE and Spring Framework applications to a Liberty server or cluster, using the WebSphere Administrative Console and/or automation with wsadmin scripts. Whether you're modernizing legacy systems or building cloud-native apps, this lab is your launchpad into the next generation of enterprise application management.

---
# Getting started

This section guides you through the initial setup of the lab environment. Perform all tasks from the student virtual machine.

## Lab environment overview

The lab environment is preinstalled with the following packages:

* WebSphere Application Server Network Deployment (ND), version 9.0.5.28+, running on Java SE 8

    * Modernized Runtime Extension for Java (MoRE), version 1.0.3.0+

* WebSphere Liberty, version 26.0.0.6+, running on Java SE 17+

In addition, the environment is preconfigured with the following profiles and server instances:

* A Deployment Manager (`dmgr`), which serves as the central controller for the WebSphere cell.
## Create a Managed Liberty Server
After the instllation, follow this steps to create a Managed Liberty Server `demo`.
1.  Launch the **WAS Admin Console** by selecting it from your browser bookmarks or navigating to the https://localhost:9043/ibm/console URL.
2. Go to **Servers** &rarr; **Server Types** &rarr; **WebSphere Application Servers** &rarr;<ins>New...</ins>.
<img width="842" height="347" alt="image" src="https://github.com/user-attachments/assets/0885e960-8699-42e4-a142-496cac9fa47a" />

4. In the `Application servers` panel,  
* Under **New...**, select **Managed Liberty server** and type `demo` under the `Server name` textbox.
<img width="1676" height="655" alt="image" src="https://github.com/user-attachments/assets/8a1dd541-d052-45e1-8e39-0dfac6987926" />

4. Click **Next** on Step 2 and 3.
5. Click **Finish** on Step 4.
6. Click **Save** on the displayed message.
<img width="1481" height="911" alt="image" src="https://github.com/user-attachments/assets/d1cdf427-4153-449e-9951-89d0f45c92b3" />

The next step is to deploy applications to the created Managed Liberty server.

# Deploy apps to a Managed Liberty Server
After you have completed the installation, it is time to deploy Jakarta EE 10 or Spring Framework 6.x apps to your Managed Liberty Servers. This downloads contains a couple of apps to help you get started.
## A Jakarta EE 10 application
The app [modResort](https://github.com/WASdev/more-techXchange-lab/releases/download/0.0.1/modresorts-2.0.0.war) utilises Jakarta EE 10 technologies. Clicking the above link to the app to download this war to your local system. The source code can be found [here](https://github.com/WASdev/more-techXchange-lab/tree/main/module1/modresorts).

### Installing the application WAR file

1. Launch the **WAS Admin Console** by selecting it from your browser bookmarks or navigating to the https://localhost:9043/ibm/console URL.

2. Go to **Applications** &rarr; **New Application** &rarr; <ins>New Enterprise Application</ins>.

<img width="1374" height="743" alt="image" src="https://github.com/user-attachments/assets/4e06461f-d54b-4ed7-a883-375bb1b129fb" />


4. In the installation panel:

   * Under **Path to new application**, select **Local file system** and choose the WAR file `modresorts-2.0.0.war` downloaded earlier.
   * Set **Target Runtime Environment** to `Jakarta EE 10`
   
   Click **Next** and wait for the application to upload.
<img width="1372" height="746" alt="image" src="https://github.com/user-attachments/assets/38f7606f-3bbf-4db4-b8af-3c0bdb3943c4" />


5. Choose **Fast Path** and click **Next**.

6. Leave **Step 1** unchanged and click **Next**.

7. On **Step 2**, map the application module:

   * Under **Cluster and servers**, select the server `demo`.

   * Check the box next to `modresorts-2.0.0.war` and click **Apply**.

   * Confirm that the server `demo` is listed under the **Server** column for the `modresorts-2.0.0.war` module.
   
   Click **Next**.

8. On **Step 3**, confirm that the **Context Root** is set to `/resorts` and click **Next**.

9. On **Step 4**, review the installation summary and click **Finish**.

10. After the installation completes, click <ins>Review</ins>. 
   
   Select **Synchronize changes with Nodes**, and click **Save**. Click **OK** when synchronization is complete.
11. Start the Managed Liberty server `demo`, by following the following instructions.
   * Go to **Servers** &rarr; **Server Types** &rarr; **WebSphere Application Servers** &rarr;
   * Click on the checkbox next to `demo` and click on `Start` button. 
<img width="1493" height="638" alt="image" src="https://github.com/user-attachments/assets/52db489f-7c68-4c67-9608-3406f7400155" />

   Both the server and the app should be started.
11. Try out the application
   * On a terminal window, go the `demo` MLS and then display `console.log` e.g. (cat /opt/IBM/WASND/profiles/AppSrv01/managedLiberty/usr/servers/demo/logs/console.log). 
   * Find the endpoint for the `ModResort` e.g. `http://9.46.96.145:9081/resorts/`. The following should be displayed.
 <img width="1677" height="965" alt="image" src="https://github.com/user-attachments/assets/3ed0e695-8cfd-45a9-b8b5-852de829cb37" />


## A Spring Framework 6.x or Spring Boot 3.x application
The app [Spring Petclinic](https://github.com/WASdev/more-techXchange-lab/releases/download/0.0.1/spring-petclinic-3.5.0-SNAPSHOT.war) utilises Spring Framework 6.x and Jakarta EE 10 technologies. Refere to [this](https://github.com/WASdev/more-techXchange-lab/tree/main/module2#about-the-spring-petclinic-application) instruction for accessing the source code.
For deploying an application using Spring Framework or Spring Boot technologies, the compatible versions for Spring Framework are 6.x while Spring Boot versions are 3.x. Any earlier versions are not compatible with Jakarta EE 10, so the applications might not work.

You can use the same steps as documented above to install this application.

## Deploy apps to a Managed Liberty Server cluster

Follow [this instruction](https://github.com/WASdev/more-techXchange-lab/blob/main/README.md) to deploy applications to a Managed Liberty Server cluster.
