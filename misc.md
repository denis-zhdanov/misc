* [intellij](#intellij)
* [kafka](#kafka)
* [postgres](#postgres)
* [spring-security](#spring-security)

## IntelliJ

* restore 'changes' VCS tab - `IDE Settings | Version Control | Commit | Use non-modal commit interface`

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
## Spring Security

* disable security:
    ```
    @Configuration
    class SecurityConfig {
        @Bean
        fun securityFilterChain(http: HttpSecurity): SecurityFilterChain {
            return http.authorizeHttpRequests {
                it.anyRequest().permitAll()
            }.csrf { it.disable() }.build()
        }
    }
    ```
