# MevandeApi

Overview
-
MevandeApi is a Java multi-module project containing shared common libraries and helper modules for the Mall4Cloud ecosystem. The repository contains several `mall4cloud-common-*` modules and supporting Docker Compose resources to run dependent services locally.

Project layout (top-level)
-
- `mall4cloud-common-core/` — core common utilities and configuration
- `mall4cloud-common-order/` — order-related common code
- `mall4cloud-common-rocketmq/` — RocketMQ helper code
- `mall4cloud-common-security/` — security-related common code
- `docker-compse/` — Docker Compose files and service configuration for local dev (note: directory name is `docker-compse`)
- various top-level Java files (e.g. `AccountClient.java`, `PayNotifyBO.java`)

Prerequisites
-
- Java JDK 11 or newer
- Maven 3.6+ (or compatible)
- Docker & Docker Compose to run containerized dependencies (if desired)

Build
-
From the repository root run:

```
mvn clean install -DskipTests
```

This builds the modules and produces artifacts in each module's `target/` folder.

Running services
-
- If the project contains Spring Boot services, run the appropriate module's `main()` or execute the produced jar in `target/`:

```
java -jar path/to/module/target/your-service.jar
```

- To start local infrastructure (MySQL/Elasticsearch/Nacos/RocketMQ/etc.) used by the project, use the Docker Compose files under `docker-compse/`:

```
cd docker-compse
docker compose up -d
```

Notes
-
- The repository contains preseed SQL and config files under `docker-compse/mysql/initdb/` and other service config directories — review them before starting containers.
- Module-specific details (ports, application properties, Spring profiles) live inside each module under `src/main/resources` and the `target/classes` outputs.

Contributing
-
If you plan to contribute, create a branch, implement changes, run `mvn clean install`, and open a pull request describing your changes.

License
-
This repository does not include a license file. Add one if you intend to make this project open source.
