FROM postgres:13

# db 초기 정보 및 db 설정 파일 복사
COPY ./init/init.sql /docker-entrypoint-initdb.d/
COPY ./config/postgresql.conf /etc/postgresql/custom.conf

# 계정 정보 설정
ENV POSTGRES_USER=myuser
ENV POSTGRES_PASSWORD=mypassword
ENV POSTGRES_DB=mydb

EXPOSE 5432

# 설정 파일 지정
CMD ["postgres", "-c", "config_file=/etc/postgresql/custom.conf"]

