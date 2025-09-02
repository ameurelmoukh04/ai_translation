# AI Translation API
# Running ReadyPortfolio Translation API with Ollama

This guide explains how to pull the Docker images and start the services using `docker-compose`.  

---

## 1️⃣ Prerequisites

Make sure you have the following installed:  

- [Docker](https://docs.docker.com/get-docker/)  
- [Docker Compose](https://docs.docker.com/compose/install/)

---

## 3️⃣ Pull the Docker Images

Run the following commands in the terminal:  

```bash
docker pull ameurelmoukh/fastapi-translation:latest

docker pull ollama/ollama:latest
```

---

## 4️⃣ start the containers
#copy the docker-compose.yml file into your project folder then :

Run the following commands:  

```bash
docker-compose up -d
```


## Endpoint
POST `/translate`

## Input JSON
```json
  {
    "education": "Bachelor's in Computer Science from MIT.",
    "description": "Passionate about building web applications and learning new technologies.",
    "workExperience": "Interned at TechCorp for 6 months developing React apps.",
    "skills": "laravel, react",
    "availability": "Full-time, available immediately."
}

```output json
{
"translations" : {
    "description": "Leidenschaftlich für den Aufbau von Webanwendungen und das Erlernen neuer Technologien.",
    "availability": "Vollzeit, ab sofort verfügbar.",
    "workExperience": "Praktikum bei TechCorp für 6 Monate, Entwicklung von React-Anwendungen.",
    "education": "BSc in Computer Science von MIT.",
    "jobTitle": "Softwareentwickler"
  },
  "detected_source_lang": "en",
  "target_lang": "de"
}
```exception if some value does not exist in request
in case education does not exist
{
    "detail": "Unexpected error: 400: Missing payload item: 'education'"
}

