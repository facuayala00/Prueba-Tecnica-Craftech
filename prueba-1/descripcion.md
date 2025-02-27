## Introducción 
El siguiente diagrama de red ilustra una aplicación web escalable y de alta disponibilidad desplegada en AWS. Se hace uso de servicios como Amazon S3, CloudFront, ALB, ECS, Fargate, RDS, DynamoDB y API Gateway para cumplir los siguientes requisitos:

- Soporte a cargas variables
- Alta disponibilidad (HA)
- Frontend en JavaScript
- Backend con base de datos relacional y no relacional
- Consumo de 2 microservicios externos

## Descripción del diagrama
El diseño soporta cargas variables mediante un Application Load Balancer (ALB) y Auto Scaling, garantizando alta disponibilidad (HA) con recursos distribuidos en dos zonas de disponibilidad y ajustando dinámicamente el número de tareas de ECS/Fargate según la demanda.  
Respecto a la aplicación web, el frontend se implementa como una aplicación estática en JavaScript alojada en un bucket de Amazon S3, distribuido mediante CloudFront. El backend se ejecuta en Amazon ECS y AWS Fargate, aprovechando la contenedorización para lograr escalabilidad, un enfoque moderno y serverless. Este backend interactúa con bases de datos relacionales (Amazon RDS) y no relacionales (Amazon DynamoDB), y consume dos microservicios externos a través de Amazon API Gateway.

## Decisiones de diseño
- Elegí Amazon ECS y AWS Fargate sobre EC2 por su enfoque moderno en contenedores, escalabilidad serverless y menor gestión de infraestructura, mejorando soluciones distribuidas. 
- Incluí una VPC para asegurar aislamiento y seguridad de los recursos, ya que se alinea con los estandares de AWS. 
- Opté por un Application Load Balancer (ALB) en lugar de un Elastic Load Balancer (ELB) por su soporte avanzado para HTTP/HTTPS, enrutamiento basado en rutas y compatibilidad con microservicios. 
- El Auto Scaling decidí representarlo como parte del flujo entre el ALB y las subnets para indicar su rol de gestion y escalamiento de tareas de ECS/Fargate, asegurando cargas variables y alta disponibilidad.

## Conclusión 
Esta arquitectura utiliza los servicios distribuidos de AWS—CloudFront, ECS/Fargate y bases de datos distribuidas en distintas zonas para entregar una aplicación web escalable, altamente disponible y eficiente, cumpliendo todos los requisitos con un diseño moderno y práctico.



