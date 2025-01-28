# Configurar cluster local con Minicube
Kubernetes es una plataforma de código abierto para administrar contenedores. Fue desarrollada por Google y actualmente es mantenida por la Cloud Native Computing Foundation1. Kubernetes facilita la automatización y configuración declarativa de cargas de trabajo y servicios.

## Configuración de Kubernetes en tu máquina local
Para trabajar con Kubernetes en un entorno local, se requieren dos herramientas esenciales:

- **CubeCtl:** permite la comunicación con el clúster.
- **MiniCube:** despliega una instancia de Docker para simular el entorno de Kubernetes.

### Instalación de CubeCtl
Para instalar CubeCtl en macOS usando HomeBrew, simplemente ejecuta:  

```bash
brew install kubectl
```

### Instalación de MiniCube
Similarmente, para instalar MiniCube usando HomeBrew:
```bash
brew install minikube
```

## Inicializar tu clúster con MiniCube
Ya con las herramientas instaladas, el siguiente paso es inicializar el clúster. Esto lo logras ejecutando:
```bash
minikube start --driver=docker
```
Este comando utiliza Docker como driver por defecto, pero MiniCube te permite trabajar con otros hypervisors como HyperB o VirtualBox, dependiendo de tu sistema operativo.

## Funcionalidades de MiniCube

MiniCube no solo facilita la creación de clústers, sino que también cuenta con utilidades adicionales:
- Crear clústers multinodo.
- Configurar un dashboard de manera sencilla.
- Exponer servicios a través de tunelización.

Además, puedes listar los plugins disponibles con:
```bash
minikube addons list
```

Para mejorar aún más la funcionalidad, puedes habilitar ciertos complementos como el 'registry' y el 'Metric Server':
```bash
minikube addons enable registry
minikube addons enable metrics-server
```

## Interactuar con tu clúster local
Una vez completada la configuración, puedes ejecutar comandos básicos para interactuar con tu clúster local. Por ejemplo, para ver los nodos:
```bash
kubectl get nodes
```

Para gestionar y visualizar las imágenes de Docker dentro de tu clúster, puedes ejecutar:
```bash
docker images
```

Para comprobar el contexto del clúster y cambiar entre diferentes contextos, utiliza:
```bash
kubectl config get-contexts
kubectl config use-context &amp;amp;amp;amp;lt;nombre-contexto&amp;amp;amp;amp;gt;
```

## Desplegar aplicaciones en Kubernetes
Puedes desplegar aplicaciones en tu entorno de Kubernetes de forma rápida. Por ejemplo, para desplegar una imagen de prueba:
```bash
kubectl run hello-cloud --image=nginx
```

Luego, verifica el estado de tus pods con:
```bash
kubectl get pods
```

## Usar el dashboard de Kubernetes?
MiniCube te permite interactuar con Kubernetes a través de un dashboard web. Puedes acceder a él con el siguiente comando:
```bash
minikube dashboard
```

Esto abrirá una URL en tu navegador, donde podrás visualizar tus pods, deployments y más, ofreciendo una representación gráfica del funcionamiento interno de Kubernetes.

## Referencias
- [Minikube start](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fmacos%2Farm64%2Fstable%2Fbinary+download)
- [Install Tools Kubernetes](https://kubernetes.io/docs/tasks/tools/)
