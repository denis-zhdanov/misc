* [cockroachdb](#cockroachdb)
* [firebase](#firebase)
* [intellij](#intellij)
* [kafka](#kafka)
* [postgres](#postgres)
* [spring-di](#spring-di)
* [spring-security](#spring-security)

## CockroachDB

* use `org.postgresql:r2dbc-postgresql` r2dbc driver instead of `io.r2dbc:r2dbc-postgresql`

## Firebase

* default password from debug android keystore is `android`
* it was necessary to register the both SHA-1 and SHA-256 certificate fingerprints in firebase project in order to be able to sign in via google

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
## Spring DI
* scan classpath components - org.springframework.context.annotation.ComponentScanAnnotationParser.parse()
* preinstantiate singletones - org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons()
* auto configurations loading and filtering - `org.springframework.boot.autoconfigure.AutoConfigurationImportSelector.AutoConfigurationGroup.process()`

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
