[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.umccr.java/gatk-bwamem-jni/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.umccr.java/gatk-bwamem-jni)

# gatk-bwamem-jni
JNI code for bwa mem.

This project builds dynamic libraries with a JNI API.
It allows Java code to call Heng Li's bwa mem aligner.

To build you'll need gmake, git, gcc, and Java 23.

#### To build and install a snapshot locally:

```
git clone --recursive https://github.com/umccr/gatk-bwamem-jni
./gradlew build
```

This will work for testing but will only include a native library for your system.
