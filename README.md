# Primer Parcial de Diseño de Sistemas UTN FRM con Java 17 - Spring Boot: Proyecto de detector de mutantes

Este proyecto tiene como objetivo desarrollar un sistema que detecte si un humano es un mutante basándose en su secuencia de ADN. El sistema ha sido diseñado siguiendo las especificaciones solicitadas.

## Descripción del Proyecto

El sistema implementa una API RESTful en Java utilizando Spring Boot. La API permite verificar secuencias de ADN y determinar si un humano es un mutante o no, siguiendo las reglas específicas de secuencias de bases nitrogenadas.

## Funcionalidades

- **Detección de Mutantes**: Implementa un método `isMutant(String[] dna)` que determina si una secuencia de ADN pertenece a un mutante. La detección se realiza buscando más de una secuencia de cuatro letras iguales, de forma horizontal, vertical u oblicua.

- **API REST**: 
  - **POST** `/mutant/`
    - **Request Body**: 
      ```json
      {
        "dna": ["ATGCGA","CAGTGC","TTATGT","AGAAGG","CCCCTA","TCACTG"]
      }
      ```
    - **Respuestas**: 
      - `200 OK` si es mutante
      - `403 Forbidden` si no es mutante

- **Estadísticas**: Exposición de un endpoint adicional `/stats` que devuelve estadísticas sobre las verificaciones de ADN.
  - **GET** `/stats/`
    - **Response Body**: 
      - `200 OK`
      ```json
      {
        "count_mutant_dna": 40,
        "count_human_dna": 100,
        "ratio": 0.4
      }
      ```

- **Base de Datos**: Utiliza H2 para almacenar las secuencias de ADN que son humanas, asegurando que solo se registre una por ADN.

## Requisitos

- Java 17
- Spring Boot
- H2 Database
- JMeter para pruebas de carga

## Instalación

1. Clona este repositorio:
   ```bash
   git clone https://github.com/Agus1097/dna.git

2. Navega al directorio del proyecto

3. Compila y ejecuta la aplicación:
   ```bash
   ./mvnw spring-boot:run

## Pruebas

Realiza pruebas automáticas para verificar la funcionalidad del sistema y asegurarte de que la cobertura de código supere el 80%. Puedes usar JMeter para simular diferentes niveles de carga y evaluar el rendimiento del sistema.

