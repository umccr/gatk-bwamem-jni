![Maven Central Version](https://img.shields.io/maven-central/v/org.umccr.java/gatk-bwamem-jni)

# gatk-bwamem-jni
JNI code for bwa mem.

This project builds dynamic libraries with a JNI API.
It allows Java code to call Heng Li's bwa mem aligner.

To build you'll need gmake, git, gcc, and Java 17.

#### To build and install a snapshot locally:

```
git clone --recursive https://github.com/umccr/gatk-bwamem-jni
./gradlew build
```

This will only include a native library for your system (or CI/CD runner).
