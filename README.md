# broadsea-achilles

![Last Version](https://img.shields.io/github/v/release/OHDSI/Broadsea-Achilles)
![License](https://img.shields.io/github/license/OHDSI/Broadsea-Achilles)
![Docker Pull](https://img.shields.io/docker/pulls/ohdsi/broadsea-achilles)
![CI](https://github.com/OHDSI/Broadsea-Achilles/actions/workflows/ci.yaml/badge.svg)

Run [OHDSI Achilles](https://github.com/OHDSI/Achilles) as a container.

```sh
docker run \
    -e ACHILLES_DB_URI="postgresql://host.docker.internal:5432/postgres" \
    -e ACHILLES_DB_USERNAME="postgres_user" \
    -e ACHILLES_DB_PASSWORD="postgres_password" \
    docker.io/ohdsi/broadsea-achilles:master
```

You are encouraged to use the `vX.Y.Z` image tags corresponding to the [releases](https://github.com/OHDSI/Broadsea-Achilles/releases) instead of using `master`.

## Configuration

The Broadsea Achilles container can be configured by passing the following environment variables:

| Environment Variable  | Description                                                                                                                                                                                        | Default value                            |
| --------------------- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ---------------------------------------- |
| ACHILLES_SOURCE       | String name of the data source name. If blank, CDM SOURCE table will be queried to try to obtain this.                                                                                             | `"unknown"`                              |
| ACHILLES_DB_URI       | The database connection string including DBMS type, host, port, and database name.                                                                                                                 | `"postgresql://localhost:5432/postgres"` |
| ACHILLES_DB_USERNAME  | The username to connect to the database. If unset, this value is retrieved from the `ACHILLES_DB_URI`.                                                                                             | `""`                                     |
| ACHILLES_DB_PASSWORD  | The password to connect to the the database. If unset, this value is retrieved from the `ACHILLES_DB_URI`.                                                                                         | `""`                                     |
| ACHILLES_CDM_SCHEMA   | Fully qualified name of database schema that contains OMOP CDM schema. On SQL Server, this should specify both the database and the schema, so for example, on SQL Server, `cdm instance.dbo`.     | `"public"`                               |
| ACHILLES_VOCAB_SCHEMA | String name of database schema that contains OMOP Vocabulary. Default is. On SQL Server, this should specify both the database and the schema, so for example `results.dbo`.                       | `"public"`                               |
| ACHILLES_RES_SCHEMA   | Fully qualified name of database schema that we can write final results to. On SQL Server, this should specify both the database and the schema, so for example, on SQL Server, `cdm results.dbo`. | `"public"`                               |
| ACHILLES_OUTPUT_BASE  | Directory for storing the analysis results in JSON format. Type "ignore" to skip JSON export.                                                                                                      | `"/opt/achilles/workspace"`              |
| ACHILLES_CDM_VERSION  | Define the OMOP CDM version used: currently supports v5 and above. Use major release number or minor number only (e.g. 5, 5.3)                                                                     | `"5"`                                    |
| ACHILLES_NUM_THREADS  | The number of threads to use to run Achilles in parallel.                                                                                                                                          | `"1"`                                    |
