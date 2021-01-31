# Project description

Demonstration project with required technologies and tools.

Project is composed from 2 services:

- REST API as a backend service; used as a communication service between User Interface and Database
- User Interface as frontend service; used as a medium for a user (e.g. medical personnel) to input patient info and their diagnosis.

# Tools and Technologies

Required technologies for this project:

- Java,
- Maven,
- Spring Framework (SpringBoot, SpringData, SpringSecurity)
  - SpringSecurity used JWT authentication
- Angular (Angular Material, and Angular Flex-Layout)
- MySQL and Flyway for database migrations
- Swagger (used Swagger2)
- Unit tests (used jUnit5)

# Download

- Download repository and its submodule repositories

```
git clone --recurse-submodules https://github.com/Carcair/MedicalCardApp-parent.git
```

- Or use:

```
git clone https://github.com/Carcair/MedicalCardApp-parent.git
git submodule init
git submodule update
```

# Installation

Demonstration project, user should have installed MySQL, and create database „medical_card_app“, and a user with all privileges on that database with credentials, user: „dev“, password: „password“.

On backend service startup, Flyway will create necessary tables in your database.

## Backend service installation

Open terminal in root folder.

```
cd medicalCardApp
mvn clean install
```

Start jUnit5 tests:

```
mvn test
```

Run REST API:

```
mvn exec:java -Dexec.mainClass="com.emird.medicalCardApp.MedicalCardAppApplication"
```

Visit Swagger API documentation on http://localhost:8080/swagger-ui.html#/

## Frontend service installation

Open terminal in root folder.

```
cd medicalCardApp-UI
npm install
```

After this we have 2 options:

- run in development mode:

```
ng serve
```

- build production version and run it:

```
ng build --prod
node server.js
```

Default url interface is running at is: http://localhost:4200

# References

Submodules located at:

- Backend service at: https://github.com/Carcair/medicalCardApp
- Frontend service at: https://github.com/Carcair/medicalCardApp-UI

# Notes, todos, and fixes (review and introspection)

1. Docker not used in project, because it wasn't included in required technologies. Future implementation possible if required.
2. UI uses basic field validations, only for empty fields. Further validation could include regex and more complicated validations.
3. Backend service (Java project) doesn't include variable validations. My preferences is to avoid as much heavy process tasks in backend service. If necessary it can be implemented by using Util services with methods for validation.
   - If implemented we could create more jUnit5 tests, to unit test those validations, which would be much more simpler to present than current tests.
4. Unit tests are lacking Exception throw testing. Lacking in precise knowledge about exceptions. Need further study to implement.
5. MySQL connection depends on every developer included in project to implement MySQL on http://localhost:3306 , and create DB and DB user according to Installation specifications, before Flyway can do migration and version control of DB. Search for mor dynamic solution for this problem.
6. Used Java integrated Flyway instead of standalone. Didn't have foresight to ask which one to use. Possible implementation of standalone Flyway integration.
7. For SpringData we used JPA and JDBC, for different purposes, instead of raw SQL queries. Implementation possible if required.
8. UI doesn't use @angular/forms modules, but manual approach of Form processing. Wasn't aware of its existence until later stages of project.

!!! Note to self:

- Review code after further study of these topics:
  - unit testing
  - exceptions
  - patterns
