# 🚀 Proyecto PruebaDummy: Despliegue en Kubernetes (VER PDF "Jhostter Valdez - Prueba Dummy")

Este repositorio contiene la configuración necesaria para el despliegue de una aplicación **Fullstack (React, Express, MySQL)** en un clúster de **Kubernetes (Minikube)**, utilizando **Azure Pipelines** para la automatización de CI/CD.

## 🏗️ Arquitectura del Sistema

La solución se basa en una arquitectura de microservicios orquestada por Kubernetes, garantizando alta disponibilidad y escalabilidad.



### Componentes de Infraestructura (Carpeta `/environment`):

* **Deployment (`deployment.yaml`)**: Gestiona 2 réplicas de la aplicación Node.js (`jhostterv/pruebadummy:latest`). Se ha configurado el puerto **80** basándose en la inspección de variables de entorno del contenedor.
* **Service (`service.yaml`)**: Un servicio tipo `ClusterIP` que actúa como balanceador interno, exponiendo el puerto 80 hacia el Ingress.
* **Ingress (`ingress.yaml`)**: Punto de entrada externo que gestiona el tráfico hacia el dominio virtual **pruebadummy.info**.

---

## 🛠️ Guía de Despliegue (Local)

Para replicar este entorno en Minikube, siga estos pasos:

### 1. Requisitos Previos
* Minikube instalado y corriendo.
* Addon de Ingress habilitado: `minikube addons enable ingress`
* Túnel activo: `minikube tunnel` (en una terminal aparte).

### 2. Aplicar Manifiestos
Navegue a la carpeta del proyecto y ejecute:
```bash
kubectl apply -f environment/

---

## ☁️ Plus: Despliegue en la Nube (Azure Container Apps)

Como valor agregado, se ha realizado el despliegue de la solución en **Azure**, utilizando el servicio **Azure Container Apps**. Esto demuestra la portabilidad de la imagen Docker creada y la capacidad de gestionar entornos productivos en la nube.

### Detalles del Despliegue en Azure:
* **Servicio**: Azure Container Apps (Serverless Container Service).
* **Ingress de Azure**: Habilitado para tráfico externo (puerto 80).
* **Escalabilidad**: Configurado para auto-escalado basado en demanda HTTP.
* **Continuous Deployment**: Integrado con los artefactos generados por el Pipeline.

> **Nota**: El uso de Container Apps permite prescindir de la gestión manual del clúster (Control Plane), enfocándose en la disponibilidad de la aplicación y la eficiencia de costos.
