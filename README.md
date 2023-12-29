
# DDD Base Structure for Symfony Projects

## Table of Contents

1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
   1. [Application](#application)
   2. [Domain](#domain)
   3. [Infrastructure](#infrastructure)
   4. [Http](#http)
3. [Layer Communication Structure](#layer-communication-structure)
3. [Usage](#usage)
4. [Contribution](#contribution)
5. [License](#license)

## Introduction

This template serves as a foundation for projects utilizing a Domain-Driven Design (DDD) architecture with Symfony. It provides a clear and modular structure, suitable for complex applications, by separating concerns and fostering better code organization.

## Project Structure

### Application

- **Command** : Contains the commands representing specific actions within the application.
- **WebService** :
  - **Assembler** : Ensures the transformation of domain entities into Data Transfer Objects (DTOs) and vice versa.
  - **DTO** : Defines the data transfer objects for communication between layers.
  - **Services** : Application services orchestrating high-level operations and coordination of workflows.

### Domain

- **Event** : Defines domain events, reflecting significant changes within the application.
- **Exception** : Customizes exceptions related to business logic.
- **Model** : Contains domain entities and value objects that encapsulate business logic.
- **Port/SPI** : Defines interfaces (Service Provider Interface) for integration with external services or other layers.

### Infrastructure

- **Database** :
  - **DataFixtures** : Scripts to initialize the database with test or startup data.
  - **DoctrineModel** : Doctrine mappings for the persistence layer.
  - **Migrations** : Manages database migrations.
- **Repositories** : Concrete implementations of repository interfaces defined in the domain layer.
- **Security** : Configuration and utilities related to the application's security.

### Http

- **Controller** : Controllers to handle HTTP requests and interact with the application layer.
- **Static** : Contains static assets like JavaScript and CSS files.
- **Templates** : Twig templates for view generation.

## Layer Communication Structure
HTTP ↔ Application: The HTTP layer directly interacts with the Application layer. HTTP controllers receive user requests and call upon application services to process these requests.

Application ↔ Domain: The Application layer utilizes entities and services from the Domain layer to execute business logic. It can also trigger domain events.

Application ↔ Infrastructure: The Application layer can interact with the Infrastructure layer to access data (via repositories) and utilize other infrastructure services (like messaging or logging).

Domain ↔ Infrastructure: Although the Domain layer is primarily isolated, it can interact with the Infrastructure through interfaces defined in the Domain but implemented in the Infrastructure (such as repository interfaces).

## Usage

To use this base structure, clone the repository and install dependencies via Composer. Adapt each layer according to the specific needs of your project.
