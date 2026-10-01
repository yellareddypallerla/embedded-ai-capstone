# osgi-service

Phase 2. Java OSGi wrapper around the kernel driver from `kernel-driver/`.
Same OSGi concepts as the real employer driver-bundle work, practiced
here first on a project you fully control.

## Setup

Apache Felix, standalone:

```bash
wget https://felix.apache.org/.../org.apache.felix.main-distribution.tar.gz
tar -xzf org.apache.felix.main-distribution-*.tar.gz
cd felix-framework-*/bin
java -jar felix.jar
```

## Starter interface

```java
public interface SensorService {
    void open();
    void close();
    byte[] readFrame();
    SensorStatus getStatus();
}
```

`Activator.start(BundleContext ctx)` registers the implementation via
`ctx.registerService(SensorService.class, new SensorDriverImpl(), null)`.

## Build

`maven-bundle-plugin` (or `bnd-maven-plugin`) in `pom.xml` so `mvn package`
produces a properly manifested OSGi JAR
(`Bundle-SymbolicName`/`Bundle-Activator`/`Import-Package`/`Export-Package`
set correctly) -- not just a plain JAR.

## Status

Not started. Depends on `kernel-driver/` having something real to wrap.
