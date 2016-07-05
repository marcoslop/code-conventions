# External libraries

### Lombok

Use Lombok whenever is possible:

- @Data
- @Setter @Getter
- @Builder
- @Sl4j

### Logger

When using Logger never concatenate strings. Use this way instead:

Insteado of using:

    log.info("Generating pages for day: "+prefix+" Sorteos: "+sorteos.size());
    

Use this way:

    log.info("Generating pages for day: {} Sorteos: {}", prefix, sorteos.size());