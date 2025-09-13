# AI Translation API

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
docker pull ameurelmoukh/fastapi_translation:latest

docker pull ollama/ollama:latest

ollama run zongwei/gemma3-translator:4b
```

---

## 4️⃣ start the containers

Run the following commands:  

```bash
docker-compose up -d
```


## Endpoint
POST `/translate`

## Input JSON
```json
{
    "firstname": "Hatim",
    "avatar": "http://localhost:5000/api/v1/storage/images/download/68cbfa95-6cf6-4d04-8653-112d3d131fe0.jpg",
    "lastname": "Anass",
    "email": "anass1997hatim@gmail.com",
    "phone": "+212691579907",
    "dateOfBirth": 838771200000,
    "placeOfBirth": "Casa Milà, Barcelone",
    "gender": "m",
    "yearsOfExperience": 0,
    "personalSkills": [
            "Teamwork Creativity Decision-Making Time Management"
],
        "skills": [ 
            "Teamwork Creativity Decision-Making"
],
        "experiences": [
        {
            "id": 1002,
            "jobTitle": "software engenier",
            "employer": "Oracle",
            "startDate": 1722380400000,
            "endDate": 1785452400000,
            "otherSubCategory": "",
            "description": [
            "Maintenance and further development of existing applications Coordination with external agencies and service providers Realization of orders"
                ],
            "jobCategory": {
                    "id": 5,
                    "label": "IT and Technology"
            },
            "jobSubCategory": {
                "id": 401,
                "label": "System Administrator",
                "jobCategory": {
                    "id": 5,
                    "label": "IT and Technology"
                }
            }
        }
],
        "educations": [
            {
                "id": 1002,
                "specialization": "facultes de medecine",
                "institute": "FSAC",
                "degree": "Licence Professionnelle",
                "startDate": 1722380400000,
                "endDate": 1785452400000
            }
],
        "languagesWithGrades": [
            "English - A1"
],
"drivingLicenses": [
"A",
"B"
]
}

```output json
{
    "tanslations": {
        "experiences": [
            {
                "jobTitle": "Software Ingenieur",
                "description": "Wartung und Weiterentwicklung bestehender Anwendungen; Koordination mit externen Agenturen und Service-Providern; Umsetzung von Aufträgen.",
                "jobCategory": "IT und Technologie",
                "jobSubCategory": "Systemadministrator"
            }
        ],
        "personalSkills": [
            "Teamarbeit Kreativität Entscheidungsfindung Zeitmanagement"
        ],
        "skills": [
            "Teamwork Kreativität Entscheidungsfindung"
        ],
        "educations": [
            {
                "specialization": "Fakultät für Medizin",
                "degree": "Master of Science (MSc)"
            }
        ]
    },
    "detected_source_lang": "en",
    "target_lang": "de"
}

```exception if some value does not exist in request
in case education does not exist
{
    "detail": "Unexpected error: 400: Missing payload item: 'educations'"
}
