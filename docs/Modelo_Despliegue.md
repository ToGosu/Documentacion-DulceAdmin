## Modelo de Despliegue – DulceAdmin

### Descripción General
El **modelo de despliegue** del sistema **DulceAdmin** define la distribución física y lógica de los componentes que conforman la aplicación.  
Esta arquitectura combina el uso de **contenedores Docker**, **servicios PaaS** y **módulos externos** para garantizar seguridad, escalabilidad y mantenimiento sencillo.

---

### Componentes Principales

- **Frontend (Vue.js):** Interfaz de usuario alojada en un servicio PaaS (Vercel o Netlify).  
- **Backend (Spring Boot):** Aplicación ejecutada dentro de un contenedor Docker, desplegada en un servicio como Render o Railway.  
- **API Gateway:** Punto de entrada de todas las solicitudes externas, que gestiona rutas y políticas de seguridad.  
- **Identity Management:** Módulo de autenticación y autorización (Auth0, Keycloak).  
- **Database (PostgreSQL):** Servicio gestionado en la nube para persistencia estructurada.  
- **Blob Storage:** Almacenamiento de archivos, recibos e imágenes (Azure Blob o Cloudinary).  
- **Bloque Transversal:** Encargado de la trazabilidad, métricas y monitoreo (Grafana, Prometheus o Elastic Stack).  
- **Integraciones externas:** Pasarelas de pago, notificaciones y catálogo de mensajes.

---

### Flujo de Comunicación

1. El usuario accede al sistema a través de Internet.  
2. El tráfico pasa por el **WAF**, que filtra peticiones maliciosas.  
3. El **Identity Management** autentica y autoriza al usuario.  
4. Las peticiones válidas llegan al **API Gateway**, que se comunica con el **Backend**.  
5. El **Backend** procesa la lógica de negocio y consulta la **Base de Datos** y el **Blob Storage**.  
6. Los registros de actividad se envían al **Bloque Transversal** para monitoreo.  
7. En caso necesario, el **Backend** se conecta con servicios externos (pasarela de pago o notificaciones).

---

### Entornos de Despliegue Recomendados

| Componente | Entorno | Servicio Sugerido |
|-------------|----------|-------------------|
| Frontend | PaaS | Vercel / Netlify |
| Backend | Docker container | Render / Railway |
| Database | Base de datos gestionada | Supabase / ElephantSQL |
| Blob Storage | Almacenamiento en nube | Cloudinary / Azure Blob |
| Identity Management | Autenticación | Auth0 / Keycloak |
| Observabilidad | Monitoreo | Grafana + Prometheus |

---

### Diagrama del Modelo de Despliegue

![Modelo de Despliegue – DulceAdmin](img/ArquitecturaReferencia.png)
![Modelo de actividades](img/ArquetipoReferencia.png)


---

### Conclusión

El **modelo de despliegue de DulceAdmin** combina servicios gestionados y contenedores para ofrecer una infraestructura ágil, modular y segura.  
Este enfoque permite escalar fácilmente el sistema, simplificar el mantenimiento y asegurar una experiencia estable para los usuarios finales.