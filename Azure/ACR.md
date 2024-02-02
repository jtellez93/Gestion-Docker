# Guía para Ejecutar una Imagen Docker en una Instancia de Cómputo de Azure
## Configuración en la Máquina Local con la Imagen Docker:

### 1. Iniciar Sesión en Azure Container Registry (ACR):
```bash
docker login <nombre_del_acr>.azurecr.io
```
`<nombre_del_acr>.azurecr.io` = Login server del ACR
Ingresa el nombre de usuario y la contraseña tomados de `Settings -> Access key` en el recurso de Azure (ACR).

### 2. Etiquetar la Imagen:
```bash
docker tag <nombre_imagen>:tag login_server/proyecto/nameimage:version
```
Ejemplo:
```bash
docker tag myimage:20210106 myregistry.azurecr.io/samples/myimage:20210106
```
queda etiquetado con el `login server` del ACR, luego un proyecto `samples` luego la imagen y la versión `myimage:20210106`
### 3. Push de la Imagen a ACR:
```bash
docker push myregistry.azurecr.io/samples/myimage:20210106
```
La imagen ahora está registrada en Azure Container Registry.

## Configuración en la Instancia de Cómputo en Azure:
### 4. Instalar la CLI de Azure:
```bash
sudo apt-get update
sudo apt-get install azure-cli
```
### 5. Iniciar Sesión en ACR desde la Instancia de Cómputo:
```bash
sudo az acr login --name <nombre_del_acr>
```
Ingresa el nombre de usuario y la contraseña tomados de `Settings -> Access key` en el recurso de Azure (ACR).
### 6. Pull de la Imagen desde ACR a la Instancia de Cómputo:
```bash
docker pull myregistry.azurecr.io/marketing/campaign10-18/email-sender:v2
```
### 7. Ejecutar el Contenedor en la Instancia de Cómputo:
```bash
docker run -p 8000:8000 myregistry.azurecr.io/marketing/campaign10-18/email-sender:v2
```
Elige un puerto local (por ejemplo, 8000) para mapear al puerto del contenedor (8000 en este caso).
