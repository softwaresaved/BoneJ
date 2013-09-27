
Standalone ANT build and test scripts
=====================================

Dependencies
============

Imglib
------

There is a compile error that ANT gives rise to:

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

Both the missing classes are available in:

legacy-imglib1-2.0.0-SNAPSHOT.jar

available via:

http://fly.mpi-cbg.de/~preibisch/software.html
http://fly.mpi-cbg.de/preibisch/software/legacy-imglib1-2.0.0-SNAPSHOT.jar

It's unclear why this problem does not occur within Eclipse.

Hamcrest and JUnit
------------------

To compile and run tests requires JUnit and Hamcrest JARs.
These are located in Eclipse plugins directories e.g.

eclipse-SDK-4.2.2-win32-x86_64/eclipse/plugins/org.hamcrest.core_1.1.0.v20090501071000.jar
eclipse-SDK-4.2.2-win32-x86_64/eclipse/plugins/org.junit_4.10.0.v4_10_0_v20120426-0900/junit.jar

Or can be downloaded from JUnit (http://junit.org/)'s GitHub repository:

https://github.com/junit-team/junit/wiki/Download-and-Install

Tested platforms
================

Tested on Windows 7 Enterprise with

Java 1.7.0_21
Apache ANT 1.9.2
JUnit 4.11
Hamcrest Core 1.3
Imglib 1 2.0.0
