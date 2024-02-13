# pom.xml
## Тег dependencies

Содержит список артефактов от которых зависит данный проект.
## Тег dependencyManagement

Используется в родительском pom файле для задания версий артефактов от которых зависит проект потомок. В этом случае в проекте потомке версии артефактов можно не задавать.

# Spring и Maven

Запуск Spring Boot приложения через Maven.

```shell
mvn spring-boot:run -Dspring-boot.run.profiles=dev -Dserver.port=8080
```

## Spring BOM - Bill Of Materials

Версии зависимостей. Можно посмотреть pom.xml -> spring-boot-starter-parent -> spring-boot-dependencies -> spring-boot-dependencies -> properties. Используется механизм Maven с тегом dependencyManagement в родительском Spring Boot проекте. #Spring/BOM

#Maven