
Standalone ANT build and test scripts
=====================================

The ANT script, build.xml, and its associated properties, ant.properties,
allows BoneJ to be built and the unit tests run from outwith Eclipse.

Dependencies
============

See ant.properties for the default paths for the dependencies and
change these if necessary.

Java JDK
--------

http://www.oracle.com/technetwork/java/javase/overview/index.html
http://www.oracle.com/technetwork/java/javase/downloads/index.html

http://openjdk.java.net/
http://openjdk.java.net/install/

Make sure the JDK bin/ directory is in your PATH.

Make sure JAVA_HOME is set to the Java JDK directory e.g.
C:\Program Files\Java\jdk1.7.0_21

Java3D
------

https://java3d.java.net/
https://java3d.java.net/binary-builds.html

Make sure the JDK bin/ directory is in your PATH.

ImageJ
------

http://rsbweb.nih.gov/ij/
http://rsbweb.nih.gov/ij/download.html

ImageJ 3D Viewer
----------------

For ImageJ 1.47, this is in ImageJ/plugins/3D/ImageJ_3D_Viewer.jar

Apache ANT
----------

http://ant.apache.org/
http://ant.apache.org/bindownload.cgi

Make sure the ANT bin/ directory is in your PATH.

JUnit and Hamcrest
------------------

These are needed to compile and run JUnit unit tests.

http://junit.org
https://github.com/junit-team/junit/wiki/Download-and-Install

If you have Eclipse then these are also located in Eclipse 
plugins directories e.g.

eclipse-SDK-4.2.2-win32-x86_64/eclipse/plugins/org.hamcrest.core_1.1.0.v20090501071000.jar
eclipse-SDK-4.2.2-win32-x86_64/eclipse/plugins/org.junit_4.10.0.v4_10_0_v20120426-0900/junit.jar

Imglib
------

These are needed to avoid a compilation error.

http://fly.mpi-cbg.de/~preibisch/software.html
http://fly.mpi-cbg.de/preibisch/software/legacy-imglib1-2.0.0-SNAPSHOT.jar

There is a compile error when building BoneJ via ANT:

src\org\doube\bonej\MeasureSurface.java:87: error: cannot access RealType
List<Point3f> points = mct.getTriangles(imp, threshold,channels,
                          ^
class file for mpicbg.imglib.type.numeric.RealType not found

src\org\doube\bonej\ParticleCounter.java:979: error: cannot access Image
List<Point3f> points = mct.getTriangles(binaryImp, 128,
                          ^
class file for mpicbg.imglib.image.Image not found

The problem originates from marchingcubes.MCTriangulator in 
ImageJ\plugins\3D\ImageJ_3D_Viewer.jar.

Both the missing classes are available in 
legacy-imglib1-2.0.0-SNAPSHOT.jar.

It's unclear why this problem does not occur within Eclipse.

Tested platforms and versions
=============================

Tested on Windows 7 Enterprise with:

Oracle Java JDK 1.7.0_21 with source and target set for Java 1.6 (via ant.properties imagej.java.version) for consistency with ImageJ 1.47.
Java3D 1.5.2
ImageJ 1.47
ImageJ 3D Viewer - bundled with ImageJ 1.47
Apache ANT 1.9.2
JUnit 4.11
Hamcrest Core 1.3
Imglib 1 2.0.0

Tested on Ubuntu 12.10 with:

OpenJDK 1.6.0_27
Java3D 1.5.2
ImageJ 1.47
ImageJ 3D Viewer - bundled with ImageJ 1.47
Apache ANT 1.9.2
JUnit 4.11
Hamcrest Core 1.3
Imglib 1 2.0.0

Build commands
==============

To see a list of build commands, run

$ ant -p
