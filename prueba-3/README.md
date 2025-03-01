# Prueba 3 - CI/CD para NGINX con index.html

## Descripción.
Para esta prueba se dockeriza NGINX para servir un `index.html` y usa un pipeline CI/CD con GitHub Actions para automatizarlo. 
Cada cambio en `prueba-3/index.html` activa el pipeline, que construye la imagen con Docker Compose, la despliega y verifica el contenido con `curl`.  
Usé Docker Compose como plataforma elegida. Los resultados del pipeline se pueden apreciar en la pestaña "Actions" de GitHub.
