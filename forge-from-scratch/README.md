Forge From Scratch
========================

What is it?
-----------

This is an example of creating a fully **Java EE compliant** project **using nothing
but JBoss Forge.** Once generated, the sample project will be a standard Maven 3
Java Web project with **JPA 2.0, EJB 3.1, CDI 1.0, JSF 2.0** views for creating, reading, updating
and deleting records, and complete **JAX-RS** endpoints for all data Entities.

But that is not all! You can use Forge on your new or existing projects
to continue enhancing any application.

System requirements
-------------------

All you need to build this project is Java 6.0 (Java SDK 1.6) or better, and an installation
of JBoss Forge version 1.0.0.Beta5 or higher. To install forge, please visit: 

   [Installing Forge](https://docs.jboss.org/author/display/FORGE/Installation)

The application this project produces is designed to be run on a JBoss AS 7 or EAP 6. 
The following instructions target JBoss AS 7, but they also apply to JBoss EAP 6.
 
With the prerequisites out of the way, you are ready to build and deploy. Note that you
do not need Maven installed in order to build this application because Forge bundles
an embedded Maven 3 installation.

Generating, Building, and Deploying the application
-------------------------
 
First, you need to install JBoss Forge, via the instructions at:

   [Installing Forge](https://docs.jboss.org/author/display/FORGE/Installation)

Then, you need to run `$ forge` from the command line, or from within JBoss Tools
or by pressing CTRL-4.

Change to the directory where this README.md file is located, using the `cd` command.

     forge> cd /path/to/quickstart/forge-from-scratch/

Notice that there is a file called `generate.fsh` in this directory; run from Forge
using the `run` command:

     forge> run generate.fsh

This command will prompt you for the {project-name} (E.g: 'example'),
and will also prompt for the top level package. This should be the domain for your
organization. (E.g: 'com.example')

Next, you need to start JBoss AS 7 (or EAP 6). To do this, run
  
    $JBOSS_HOME/bin/standalone.sh
  
or if you are using windows
 
    $JBOSS_HOME/bin/standalone.bat

To build the application, type 'build', then to deploy the application, use the 
'jboss-as-7' Forge plugin; just type:

     forge> forge install-plugin jboss-as-7
	 forge> as7 setup
	 forge> as7 deploy

This will deploy `target/{project-name}.war`.
 
The application will be running at the following URL <http://localhost:8080/{project-name}/>.
You may access it at this URL, just make sure to replace {project-name} with the name of the
project you chose when running the script.

To undeploy from JBoss AS, run this command:

     forge> as7 undeploy

You can also start JBoss AS 7 and deploy the project using Eclipse. See the JBoss AS 7
Getting Started Guide for Developers for more information.

What did we create?
========================
This quickstart has set up a native Java EE 6 application. For a full description of what was generated with this script, and the structure of the application, you should visit the [Forge UI Scaffolding Guide](https://docs.jboss.org/author/display/FORGE/UI+Scaffolding)
 
Next Steps
============================
Open `generate.fsh` and take a look inside! There is not much magic happening here. All of the
commands used to generate this project are clearly listed just as if they were typed by your
own hands.

Play around with creating more entities, relationships, UI, and generating JAX-RS endpoints,
all with just a few simple commands.

Explore plugins! 
================
Forge has a rich plugin ecosystem. Want to deploy your application to the Cloud?
Use the Forge Openshift Express plugin: http://github.com/forge/plugin-openshift-express/

To see a full list of avaialable plugins, make sure that you have an active internet connection and type:

     forge> forge find-plugin *

Importing the project into an IDE
=================================

If you created the project using the Forge Console in JBoss Tools, then there is 
nothing to do; the projet should already be imported.

If you created the project from a Forge console running outside of the IDE, then
you need to import the project into your IDE. If you are using NetBeans 6.8 or
IntelliJ IDEA 9, then all you have to do is open the project as an existing
project. Both of these IDEs recognize Maven projects natively.

Downloading the sources and Javadocs
====================================

If you want to be able to debug into the source code or look at the Javadocs
of any library in the project, you can run either of the following two
commands to pull them into your local repository. The IDE should then detect
them.

    forge> mvn dependency:sources
    forge> mvn dependency:resolve -Dclassifier=javadoc