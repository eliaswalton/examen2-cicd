# examen2-cicd



\## Evidencia de Deployment - Actividad 3



\### CD Pipeline exitoso

!\[CD Pipeline](./screenshots/cd-pipeline.png)



\### Imagen en Docker Hub

!\[Docker Hub](./screenshots/dockerhub.png)



Actividad 4: Troubleshooting (3 pts)

Se proporcionan 3 snippets de YAML de workflows con errores. Tarea: identificar y corregir

cada error.

Snippet 1 (1 pt): CORREGIDO:



name: CI Pipeline

on:

push:

branches: \[main]

pull\_request:

branches: \[main, develop]

jobs:

test:

runs-on: ubuntu-latest



Snippet 2 (1 pt): CORREGIDO:

deploy:

runs-on: ubuntu-latest

environment: production

steps:

\- uses: actions/checkout@v4

\- name: Deploy to Vercel

run: vercel --prod --token $VERCEL\_TOKEN

env:

VERCEL\_TOKEN: ${{ secrets.VERCEL\_TOKEN }}



Snippet 3 (1 pt): CORREGIDO:

test:

runs-on: ubuntu-latest

strategy:

matrix:

node-version: \[16, 18]

steps:

\- uses: actions/checkout@v4

\- uses: actions/setup-node@v4

with:

node-version: ${{ matrix.node-version }}

cache: 'npm'

\- run: npm ci \&\& npm test

