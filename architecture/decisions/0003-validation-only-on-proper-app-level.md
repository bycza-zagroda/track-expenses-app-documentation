# 3. Validation of incoming application data

Date: 2023-03-07

## Status

Accepted

## Context

**What is meant by validation of data?**

Data validation means checking the accuracy and quality of source data before using, importing or otherwise processing data. Different types of validation can be performed depending on destination constraints or objectives. Data validation is a form of data cleansing.

[Validation with Spring Boot](https://github.com/bycza-zagroda/track-expenses-app-documentation/blob/develop/docs/spring/Validation-with-spring-boot.md)

Validation can take place in one or many layers of the application, e.g.: [ _controller, data transfer object, service_ ].
Validations are usually implemented in domain entity constructors or in methods that can update the entity. There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails. There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.

[Domain Model Layer Validations](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/domain-model-layer-validations)
[Validation in Java applications](https://dzone.com/articles/validation-in-java-applications)

In order not to unnecessarily duplicate the code [**1**], it is necessary to decide whether to implement validation only on one layer of the application or maybe on many layers of the application.

## Decision

Validation will take place only on one, most appropriate layer of the application. Typically, this should be the service layer.

## Consequences

- The application code will follow the development rules [**1**].


[**1**] Principle of software development

- [DRY (Don’t Repeat Yourself)](https://github.com/bycza-zagroda/track-expenses-app-documentation/blob/develop/docs/clean-code/dry.md)
- [YAGNI (You Aren’t Gonna Need It)](https://github.com/bycza-zagroda/track-expenses-app-documentation/blob/develop/docs/clean-code/yagni.md)
