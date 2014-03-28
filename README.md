jigsaw-commons-lang3
====================

Some fun with Project Jigsaw

1) Download the early release https://jdk8.java.net/jigsaw/ (you'll want the JDK modules image)
2) Read the Quick Start http://openjdk.java.net/projects/jigsaw/doc/quickstart.html
3) Ensure you either put the jigsaw bin directory on your path or use fully qualified file paths to the executables.
Example: Using Apache Commons Lang as a module

Easy Running the example code:
1) Create a module library directory by running:
```
jmod -L moduleLib create
```

2) Install the prebuilt modules by running:
```
jmod -L moduleLib install modules/com.bobpaulin.apache.jigsaw@0.1.jmod modules/org.apache.commons.lang3@3.3.1.jmod
```

3) Run the Demo Code:
```
java -L moduleLib -m com.bobpaulin.apache.jigsaw
```

A little more fun.  Compile the modules from scratch:
1) Create a module library directory by running (if you did the example from before delete moduleLib directory):
```
jmod -L moduleLib create
```

2) Compile Apache Commons Lib
```
javac -d modules/org.apache.commons.lang3 -sourcepath common-lang-jigsaw `find common-lang-jigsaw/src/main/java -name '*.java'`
```

3) Install Apache Commons Lib
```
jmod -L mlib install modules org.apache.commons.lang3
```

4) Compile Demo Code:
```
javac.exe -d modules/com.bobpaulin.apache.jigsaw -sourcepath com.bobpaulin.apache.jigsaw `find com.bobpaulin.apache.jigsaw/src -name '*.java'`
```

5) Install Demo Code
```
jmod -L mlib install modules com.bobpaulin.apache.jigsaw
```

6) Run Demo Code
```
java -L moduleLib -m com.bobpaulin.apache.jigsaw
```

Extra Credit:
7) Packaging built modules by running:
```
jpkg -m modules/com.bobpaulin.apache.jigsaw jmod com.bobpaulin.apache.jigsaw
jpkg -m modules/org.apache.commons.lang3 jmod org.apache.commons.lang3
```

MORE EXTRA Credit:
8) Create a new bundle of an Open Source Library by creating a module-info.java in the source root:
```
module org.apache.commons.lang3 @ 3.3.1 {
    exports org.apache.commons.lang3;
}
```
