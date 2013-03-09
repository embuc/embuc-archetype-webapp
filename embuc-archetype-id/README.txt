This topic is well described on <a title="maven homepage" href="http://maven.apache.org">maven homepage</a> but if you 
are impatient or just need a quick start, here we go. There are a zillion different archetypes out there but somehow it 
more often than seldom that there is no particular type that suits exactly our needs. That's where we simply create our own.
It takes no more than 5-10 minutes to create this. I'll skip actual files as this is highly individual. However one note 
here, maven <em>will </em>skip empty folders so you could put some template files or classes if you really need these folders.

We start by creating folder structure and files that we want for our project. In this example I will create following:
[cc lang="bash" theme="default" linenumber="off"]
embuc-archetype-id -- Backend -- src
                                -- main
                                   -- java
               ... (add test folders and any template files/resources as you need)
                      pom.xml
                   -- Frontend -- src
                                -- main
                                  -- java
                                  -- webapp (add e.g. web.xml, default spring conf. etc.)
               ... (add test folders and any template files/resources as you need)
                      pom.xml
pom.xml
[/cc]

When you are happy with your project outline navigate to the root of the project (in console/bash) - 
in this case folder named embuc-archetype-id.
Run following command:
[cc lang="bash" theme="blackboard" nowrap="0" line_numbers="0"]
user@whatever_path/embuc-archetype-id:~$mvn archetype:create-from-project
[/cc]
This instructs maven to compile your archetype. If everything goes fine (what could possibly go wrong...) 
there is a compiled archetype in the target folder. Navigate there and execute following:

[cc lang="bash" theme="blackboard" nowrap="0" line_numbers="0"]
user@whateverpath/embuc-archetype-id/target/generated-sources/archetype:~$mvn install
[/cc]
This will package and install our archetype in local maven repository. Basically we are done - we can start using our archetype.
Navigate somewhere where you desire to create a prototype for a project based on our archetype and execute:
[cc lang="bash" theme="blackboard" nowrap="0" line_numbers="0"]
user@whatever_path/:~$mvn archetype:generate -DarchetypeCatalog=local
[/cc]
Maven will ask you some questions that you should answer (parameters such as group-id, artifact-id should be 
specified in your template as variables e.g. ${variable_name}) and this look like this:
[cc lang="bash" theme="blackboard" nowrap="0" line_numbers="0"]
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] &gt;&gt;&gt; maven-archetype-plugin:2.2:generate (default-cli) @ standalone-pom &gt;&gt;&gt;
[INFO]
[INFO] &lt;&lt;&lt; maven-archetype-plugin:2.2:generate (default-cli) @ standalone-pom &lt;&lt;&lt; 
[INFO] [INFO] --- maven-archetype-plugin:2.2:generate (default-cli) @ standalone-pom --- 
[INFO] Generating project in Interactive mode 
[INFO] No archetype defined. Using maven-archetype-quickstart (org.apache.maven.archetypes:maven-archetype-quickstart:1.0) 
Choose archetype: 1: local -&gt; se.embuc.groupId:embuc-archetype-id-archetype (Some description)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): : 1
Define value for property 'groupId': : my.awesome.group.id
Define value for property 'artifactId': : My new project
Define value for property 'version': 1.0-SNAPSHOT: :
Define value for property 'package': my.awesome.group.id: :
Confirm properties configuration:
groupId: my.awesome.group.id
artifactId: My new project
version: 1.0-SNAPSHOT
package: my.awesome.group.id
Y: : Y
[INFO] ----------------------------------------------------------------------------
[INFO] Using following parameters for creating project from Archetype: embuc-archetype-id-archetype:0.0.1-SNAPSHOT
[INFO] ----------------------------------------------------------------------------
[INFO] Parameter: groupId, Value: my.awesome.group.id
[INFO] Parameter: artifactId, Value: My new project
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] Parameter: package, Value: my.awesome.group.id
[INFO] Parameter: packageInPathFormat, Value: my/awesome/group/id
[INFO] Parameter: package, Value: my.awesome.group.id
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] Parameter: groupId, Value: my.awesome.group.id
[INFO] Parameter: artifactId, Value: My new project
[INFO] Parent element not overwritten in some_pah/tmp/My new project/Backend/pom.xml
[INFO] Parent element not overwritten in some_path/tmp/My new project/Frontend/pom.xml
[INFO] project created from Archetype in dir: some_path/tmp/My new project
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 29.647s
[INFO] Finished at: Tue Mar 05 23:31:45 CET 2013
[INFO] Final Memory: 11M/218M
[INFO] ------------------------------------------------------------------------
[/cc]

So, that's all, our project is created and ready. Happy coding! 
