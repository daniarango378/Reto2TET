# Reto 2: Despliegue de Wordpress en Kubernetes en Alta Disponibilidad

**Info de la materia:** ST0263: Tópicos Especiales en Telemática, 2024-2  
**Estudiantes:** Daniela Arango Gutiérrez (darangog2@eafit.edu.co)  
**Profesor:** Alvaro Enrique Ospina Sanjuan (aeospinas@eafit.edu.co)  

## 1. Descripción General

En este proyecto se despliega Wordpress en un clúster Kubernetes en la nube (AWS EKS) con alta disponibilidad, balanceador de carga, y autoescalado. Este LMS incluye un dominio personalizado con certificado SSL (`https://reto2.retoeafittelematica.online`) y está respaldado por servicios externos para bases de datos y almacenamiento de archivos.

### 1.1. Aspectos Cumplidos

- **Despliegue en Kubernetes:** Se implementó un clúster Kubernetes en AWS EKS.
- **Balanceador de carga:** Se utilizó Nginx como balanceador de carga de la aplicación.
- **Alta disponibilidad:** Tanto la capa de aplicación (Wordpress), la base de datos, y el sistema de archivos fueron diseñados para ser altamente disponibles.
- **Base de datos en Kubernetes:** La base de datos se desplegó dentro del clúster Kubernetes utilizando contenedores.
- **Almacenamiento de archivos NFS:** El servidor de archivos fue implementado como un servicio NFS dentro del clúster Kubernetes.
- **Dominio:** Se implementó un dominio específico para el reto.

### 1.2. Aspectos No Cumplidos

- **Moodle:** No se logro hacer la implementación con moodle y se uso wordpress en su lugar
- **SSL:** No se logro hacer que funcionara el certificado SSL por falta de acceso a Amazon Route 53

## 2. Diseño de Alto Nivel

El diseño de la arquitectura está basado en los siguientes componentes:

- **Kubernetes en AWS EKS:** Para orquestación de contenedores.
- **Nginx como balanceador de carga** en la capa de aplicación.
- **Base de Datos en contenedor:** Desplegada en el clúster para garantizar la disponibilidad.
- **Servidor de Archivos NFS:** Implementado en el propio clúster como sistema de archivos distribuido.
- **Certificado SSL:** Configurado en el balanceador para acceso seguro HTTPS.

## 3. Ambiente de Desarrollo

- **Lenguaje de programación:** Kubernetes Manifests (YAML), Helm para despliegue.
- **Librerías y herramientas:**  
  - Kubernetes v1.21
  - Docker v20.10.8
  - Nginx v1.20
  - AWS CLI v2
  - Helm v3.6.3
  - Cert-manager para la gestión de SSL
- **Cómo compilar y ejecutar:**
  - Configuración del clúster en AWS EKS con los manifiestos necesarios.
  - Despliegue de Wordpress con `kubectl apply -f deployement.yaml`.
  - Ejecución de scripts en Bash para configuración de parámetros del dominio y SSL.
  
### Detalles Técnicos

1. **Configuración de parámetros:**
   - **Base de datos:** Variables de entorno (`DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD`).
   - **Conexión NFS:** Parámetros de montaje en los volúmenes de los contenedores.
   - **Certificados SSL:** Configurados a través de cert-manager en Kubernetes.

## 4. Ambiente de Ejecución

- **Lenguaje y Herramientas en Producción:**
  - Kubernetes v1.21 en AWS EKS
  - Docker
  - Nginx como balanceador
  - Cert-manager para SSL
- **IP/Dominio:** `http://reto2.retoeafittelematica.online`
  
### Guía para Usuarios Finales

1. **Acceder al LMS Moodle** en `http://reto2.retoeafittelematica.online`.
2. Crear una cuenta de usuario o autenticarse para acceder a los recursos.

## 5. Otra Información Relevante

link al video sustentación: https://youtu.be/TDtpiAIJ4J4

- **Recursos:**  
  - Guías y recursos de Kubernetes: 
    - [Despliegue de Wordpress en AWS EKS](https://github.com/st0263eafit/st0263-242/tree/main/eks-wp)
    - [Video introductorio a Kubernetes](https://youtu.be/DCoBcpOA7W4)
    - [Guía de alta disponibilidad para Wordpress en Kubernetes](https://medium.com/@icheko/wordpress-high-availability-on-kubernetes-f6c0bcc2f28d)

