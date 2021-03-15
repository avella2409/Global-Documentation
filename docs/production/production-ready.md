# Production Ready Workflow

## Goal

Overview of the process to make production ready application.

## Steps

### `Be prepared`
- Plan a maximum of use case 
- What the application need to achieve ?
- Identify read process
- Identify write process
- Practice example mapping (Like cucumber spec)
- Practice event storming. Discover implication of every action

### `Make App deployable from start`
- Create git repository
- Add git machine user as collaborator of the new repository
- Dockerize app with distributed logging in mind
- Create Jenkins jobs. BUILD/RELEASE/PUSH to ECR
- Create AWS deployment process
- Deploy app with the full pipeline from commit to deploy

### `Make App flexible`
- Clean architecture / Hexagonal architecture / Port and adapter
- Create a core with an application layer and a domain layer
- Application layer contains all use cases of the application
- A use case interact with the domain layer
- Domain layer contains all domain related logic
- Create an infrastructure layer. Infrastructure layer implement all interface of the domain layer.
- Create a client layer. Client layer call the application layer.

### `Make App safe and easy to refactor`
- Use test driven development
- Wishful thinking programming. Model the code the way we wish it was already implemented. Act like all complex functionality are already implemented.
- Create unit test (From the use case)
- Create integration test
- Create e2e test

### `Folder structure production code`
- clients/
- configuration/
- core/
  . application/
  . domain/
- infrastructure/

### `Folder structure test`
- unit/
- integration/
- e2e/
- tools/


### `Unit testing strategy`
- Create a lot of test for use cases ([Outside-in diamond](https://www.youtube.com/watch?v=djdMp9i04Sc))
- Create test for the domain when it's hard to test it from the use case
- Create builder with domain specific syntax to build the use case. Make it easily composable.
- Make test easy to refactor
- Only test behavior
- Stub every infrastructure code. Create stub that implement interface of the domain layer.
- Unit test communicate only with the core of the application

### `Integration testing strategy`
- Test only adapter, one at a time (clients/infrastructure)
- Use TestContainer
- Use WireMock
- Use WebFluxTest. Mock use case.
- If we use managed service and there is a docker container doing the same use TestContainer and create a lot of test. Create only few test with the real distant managed service, test most important path.

### `E2E testing strategy`
- We want to check all the part of the application work together with the real configuration
- Use TestContainer not real distant service (Already tested in integration test)
- Use WireMock (Or cloud stub contract)
- No load balancer
- No remote config

### `Distributed Logging`
- Fluent-bit agent. Push log from file to remote server.
- Elasticsearch. Easy to visualize data with kibana and es.
- We could also use a log4j2 appender that send log to remote server.

### `Service discovery / Load balancing`
- Netflix eureka

### `Remote Config`
- Spring cloud config

### `Api Gateway`
- Spring cloud gateway

### `Api Documentation`
- Swagger

### `Monitoring`
- Prometheus