# Use a imagem do Maven com OpenJDK 21
FROM maven:3.9-eclipse-temurin-21 AS build

# Defina o diretório de trabalho dentro do container
WORKDIR /app

# Copie o código-fonte do projeto para o diretório de trabalho
COPY . .

# Compile o projeto usando o Maven e gere o arquivo JAR
RUN mvn clean package -DskipTests

# Use uma imagem do OpenJDK para rodar o JAR
FROM openjdk:21-jdk

# Defina o diretório de trabalho para o container
WORKDIR /app

# Copie o JAR gerado no estágio anterior
COPY --from=build /app/target/*.jar app.jar

# Comando para rodar o JAR no container
ENTRYPOINT ["java", "-jar", "app.jar"]

# Exponha a porta do seu Spring Boot
EXPOSE 8080
