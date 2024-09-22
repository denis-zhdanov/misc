* [postgres](#postgres)

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
