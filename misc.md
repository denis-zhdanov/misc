* [kafka](#kafka)
* [postgres](#postgres)

## Kafka

* list consumer groups - `kafka-consumer-groups --list --bootstrap-server localhost:9092`
* get consumer group info - `kafka-consumer-groups --describe --group <consumer-group-name> --bootstrap-server localhost:9092`
* list topics - `kafka-topics --list --bootstrap-server localhost:9092`

## Postgres

* show generated sql in spring - `logging.level.io.r2dbc.postgresql.QUERY=DEBUG` in `application.yml`
* return state before update - reason that it works is that multiple commands run in parallel on the same initial data snapshot:
    ```
    WITH updated_row AS (
      UPDATE <table>
      SET <update-details>
      WHERE <filter>
    )
    SELECT * from <table> WHERE <filter>;
    ```
