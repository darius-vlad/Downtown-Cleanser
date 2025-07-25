﻿# README

Humeiuc Dan-Stefan
Vlad Darius

## 1. Prezentare generala

Aplicatia este alcatuita din trei parti principale:

* **Front-End**: aplicatie mobil si web in Flutter
* **Backend**: server in SpringBoot care expune API-urile necesare
* **Model**: sunt doua modele unul de object detection (yoloV8-local) si unul de image-to-text (Gemini2.5-cloud)

 

## 2. Front-End (Flutter)

1. Trebuie sa fie instalat [Flutter SDK](https://flutter.dev) si ai setat variabila de mediu `PATH` catre executabilele Flutter.

2. Intr-un terminal 

   ```bash
   cd frontend
   ```

3. Instaleaza dependintele Flutter:

   ```bash
   flutter pub get
   ```

4. Conecteaza un emulator Android/iOS sau un dispozitiv fizic.

5. Ruleaza aplicatia:

   ```bash
   flutter run
   ```

Aplicatia Flutter va porni si va afisa interfata mobile.

 

## 3. Backend

Backend-ul este un server Java (Spring Boot). Inainte de a rula, va trebui sa fie creeat fisierul de configurare `application.properties`.

1. Trebuie Java 17+ si Maven.

2. Intrt-un treminal:

   ```bash
   cd backend
   ```

3. Creeaza fisierul de configurare `src/main/resources/application.properties`. Exemplu minimal:

   ```properties
    # Port-ul pe care ruleaza serverul
    server.port=8080

    # Configurare conexiune DB (daca este nevoie)
    spring.application.name=be_downtown-cleanser

    # JPA/Hibernate
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

    spring.datasource.url=
    spring.datasource.username=
    spring.datasource.password=

    # s3bucket
    aws.region = 
    aws.key.access =
    aws.key.secret =
    filebase.endpoint =
    filebase.bucket.name =
    filebase.gateway.name =

    security.pass.salt=

    spring.servlet.multipart.max-file-size=50MB
    spring.servlet.multipart.max-request-size=50MB

    spring.data.redis.host=
    spring.data.redis.port=
    spring.data.redis.username=
    spring.data.redis.password=

   ```

4. Instaleaza dependintele si compileaza proiectul:

   ```bash
   mvn clean install
   ```

5. Ruleaza serverul:

   ```bash
   mvn spring-boot:run
   ```

 

## 4. Model Python

Scriptul Python contine logica de machine learning. Pentru a-l rula:

1. Asigura-te ca ai instalat Python 3.13+.

2. Intr-uin terminal:

   ```bash
   cd python-model
   ```

3. Creeaza un mediu virtual si activeaza-l (optional, dar recomandat):

   ```bash
   python -m venv venv
   # pe Linux/MacOS
   source venv/bin/activate
   # pe Windows
   venv\\Scripts\\activate
   ```

4. Instaleaza dependintele din `requirements.txt`:

   ```bash
   pip install -r requirements.txt
   ```

5.
    Pt a functiona are nevioie de 3 fisier `.env`

    In folderul `model`:

        REDIS_HOST= 
        REDIS_PORT= 
        REDIS_USER= 
        REDIS_PASSWORD=
    
    In folderul `repository`:

        AWS_ACCESS_KEY_ID=
        AWS_SECRET_ACCESS_KEY=
        S3_ENDPOINT_URL=
        S3_BUCKET_NAME=
        FILEBASE_DEFAULT_GATEWAY=
        DB_HOST=
        DB_PORT=
        DB_NAME=
        DB_USER=
        DB_PASSWORD=

    In folderul `service`:

        REDIS_HOST=
        REDIS_PORT=
        REDIS_USER=
        REDIS_PASSWORD=


6. Ruleaza main.py:

   ```bash
   python main.py
   ```

## 5. Ideei de implementare
Ne-am propus sa creem o platforma care si noi am fi multumiti sa o folosim.
Video de prezentare: https://www.youtube.com/watch?v=CVywLUWnnPw
 

## 6. Note finale

Noi ne dorim sa ne hostam aplicatia, in cazul in care reusim va vom contacta ca sa va spunem ca este o varianta mai usoara de a accesa platforma.

Va multumim pt timpul acordat.
