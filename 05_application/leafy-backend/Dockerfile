# 빌드 스테이지
FROM gradle:7.6.1-jdk17 AS build
WORKDIR /app

COPY . /app
RUN gradle clean build

# 실행 스테이지
FROM eclipse-temurin:17-jre
WORKDIR /app

COPY --from=build /app/build/libs/Leafy.jar /app/leafy.jar

EXPOSE 8080
ENTRYPOINT ["java"]
CMD ["-jar", "leafy.jar"]