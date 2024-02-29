# Étape de compilation avec Maven
FROM maven AS builder

# Définir le répertoire de travail
WORKDIR /app

# Copier les fichiers de configuration Maven (pom.xml) pour télécharger les dépendances
COPY pom.xml .

# Copier le reste des sources
COPY src ./src

# Exécuter le build de l'application sans tests
RUN mvn clean install -DskipTests

# Étape de construction de l'image finale
FROM openjdk:17-jdk-slim

# Définir le répertoire de travail
WORKDIR /app

# Copier les artefacts de build depuis l'étape de compilation
COPY  target/demo-0.0.1-SNAPSHOT.jar /app.jar

# Exposer le port nécessaire pour votre application
EXPOSE 8080

# Commande de démarrage de l'application
CMD ["java", "-jar", "/app.jar"]
