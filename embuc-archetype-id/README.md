
This is a multi module maven project with two modules, one named backend contains simple Spring Boot app and other has
{React/Angular/Vue/etc} frontend. Maven builds frontend first and unpacks it and includes in building backend (boot jar
file).
During development both project can be run in separate servers (embedded tomcat for boot and express for frontend) 
independently.

# Frontend
run frontend server (from frontend folder):
### `npm run dev`

## Backend

run backend server (from backend folder):
### `mvn spring-boot:run`

## How to deploy

You can run this as executable jar (mind usage of profiles depending on the environment) e.g.:

#### Locally (jar)

`$> java  -Xmx256M -jar backend.jar &`

## Deploy with Docker

Look inside README.md in backend module for details on how to build and run docker container image with this application.


# ------ Bellow on Artifact itself - remove on creation -------

This topic is well described on the [maven homepage](http://maven.apache.org), but if you are impatient or just need a
quick start, here's how to proceed. There are many different archetypes available, but often none exactly fit our needs.
In such cases, we can create our own. It usually takes no more than 5-10 minutes to do this. I'll omit the actual files
since this is highly individual. Note that maven **will** skip empty folders, so consider adding some template files or
classes if you need those folders.

We start by creating the folder structure and files for our project. In this example, I will create the following:

```bash
embuc-archetype-id
|-- Backend
|   `-- src
|       `-- main
|           `-- java
|               ...(add test folders and any template files/resources as needed)
|           `-- kotlin
|               ...(add test folders and any template files/resources as needed)
|   `-- pom.xml
|-- Frontend
|   `-- src
|       `... here goes your frontend project
|   `-- pom.xml
`-- pom.xml
```

Once you are satisfied with your project outline, navigate to the root of the project (in console/bash) - in this case,
the folder named `embuc-archetype-id`. Run the following command:

```bash
user@whatever_path/embuc-archetype-id:~$ mvn archetype:create-from-project
```

This instructs Maven to compile your archetype. If everything goes well, the compiled archetype will be in the target
folder. Navigate there and execute the following:

```bash
user@whateverpath/embuc-archetype-id/target/generated-sources/archetype:~$ mvn install
```

This will package and install our archetype in the local Maven repository. We are now ready to use our archetype.
Navigate to where you wish to create a project prototype based on our archetype and execute:

```bash
user@whatever_path/:~$ mvn archetype:generate -DarchetypeCatalog=local
```

Maven will prompt you with some questions. You should answer these (parameters such as group-id, artifact-id should be
specified in your template as variables, e.g., `${variable_name}`). The process might look like this:

```bash
[INFO] Scanning for projects...
...
Choose archetype: 1: local -> se.embuc.groupId:embuc-archetype-id-archetype (Some description)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): : 1
Define value for property 'groupId': : my.awesome.group.id
Define value for property 'artifactId': : My new project
Define value for property 'version': 1.0-SNAPSHOT: :
Define value for property 'package': my.awesome.group.id: :
...
[INFO] BUILD SUCCESS
```

So, that's all, our project is created and ready. Happy coding!

~~~~