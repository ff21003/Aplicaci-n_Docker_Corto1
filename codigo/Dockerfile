# Imagen base de OpenJDK 17
FROM openjdk:17

# Copiar el archivo mvnw y mvnw.cmd y el directorio .mvn para usar el wrapper
COPY .mvn/ .mvn
COPY mvnw mvnw.cmd /app/

# Copiar el proyecto al contenedor
COPY . /app

# Establecer el directorio de trabajo
WORKDIR /app

# Dar permisos de ejecución al script mvnw
RUN chmod +x mvnw

# Ejecutar Maven para compilar la aplicación y empaquetar el JAR dentro del contenedor
RUN ./mvnw clean package -DskipTests

# Copiar el JAR generado dentro del contenedor
COPY target/*.jar app.jar

# Exponer el puerto 8080
EXPOSE 8080

# Comando para ejecutar el archivo JAR cuando se inicie el contenedor
ENTRYPOINT ["java", "-jar", "java-app.jar"]
