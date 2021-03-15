# Development

## Clean architecture
- Clients layer
- Core Layer/ Application layer/ Domain layer/
- Infrastructure layer
- Configuration layer

## Folder structure production code
- clients/
- configuration/
- core/ 
  . application/
  . domain/
- infrastructure/

## Folder structure test
- unit/
- integration/
- e2e/
- tools/

## BDD/TDD -> Use case testing
- Wishful thinking programming
- Test from use case (Outside-in diamond tpierrain) (application layer)
- Few fine-grained test from domain
- Stub every infrastructure code
- Make test code that can be easily refactor. Anti Fragile Test
- Only test behaviour
- Best ref = [Tpierrain Video](https://www.youtube.com/watch?v=djdMp9i04Sc)

## DDD
- Entity
- ValueObject
- Repository
- Factory
- Domain Event
- Model code to speak the same language as the domain
- Relationship need to be clear

## Env variable in properties file
- random.variable=${RANDOM_VARIABLE}

## Unit testing strategy
- A lot of test from use case
- Few test from domain for complex part or hard to test from use case part
- Refactoring in mind
- Only test behaviour
- Stub every infrastructure code

## Integration testing strategy
- Test ONLY ADAPTER, one at a time (clients/infrastructure)
- Use TestContainer
- Use wire mock
- Use webflux test (Mock service)
- If we use managed service, fake it with TestContainer and make a lot of test with it
- Few test with real distant managed service, only important path

## E2E testing strategy
- We want to see that all part work together with the real configuration but with local endpoint. Services come from TestContainer
- TestContainer
- WireMock (Or cloud stub contract)
- No load balancer
- No remote config

## TestContainer
- Setup one time launch easily every time

## Distributed Logging
- Fluent-bit
- Elasticsearch