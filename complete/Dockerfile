#FROM eclipse-temurin:17-jdk-alpine
FROM amazoncorretto:17-alpine
RUN addgroup -S spring && adduser -S spring -G spring   # mitigate some risks
USER spring:spring
ARG DEPENDENCY=target/dependency

# BOOT-INF/lib          ==  dependency JARs
COPY ${DEPENDENCY}/BOOT-INF/lib /app/lib
COPY ${DEPENDENCY}/META-INF /app/META-INF
# BOOT-INF/classes      ==  application classes
COPY ${DEPENDENCY}/BOOT-INF/classes /app
ENTRYPOINT ["java","-cp","app:app/lib/*","hello.Application"]
