---
weight: 60
---

# Debugging / troubleshooting

## Logger

The javaDataPipeline library uses *SLF4J* (Simple Logging Facade for Java).

You can either use this with the SLF4J simple logger, or it can bind to your own favourite logging framework.
In order to set the default simple logger to more verbose logging:

- add the `org.slf4j:slf4j-simple` dependency
- set the log level:

```System.setProperty(org.slf4j.impl.SimpleLogger.DEFAULT_LOG_LEVEL_KEY, "TRACE");```

## Running manually

Instead of running:

```
fair run src/main/resources/config.yaml
```

You can call `fair run` and your actual java code separately:

```
fair run --ci src/main/resources/config.yaml
gradle run --args "/tmp/tmpXXXXXXX/data_store/jobs/<timestamp>"
```

The actual tmp location is shown as output from the `fair run` command.

This may help debug/troubleshoot.

