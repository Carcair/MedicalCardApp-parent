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

## References

Submodules located at:

- Backend service at: https://github.com/Carcair/medicalCardApp
- Frontend service at: https://github.com/Carcair/medicalCardApp-UI
