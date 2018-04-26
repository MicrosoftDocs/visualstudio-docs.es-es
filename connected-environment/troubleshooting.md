---
title: Solución de problemas | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: troubleshooting
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: b41d228bcced6149c95b09b2445dd656ed9772d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-guide"></a>Guía de solución de problemas

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>Error de conexión en dirección ascendente o de desconexión/restablecimiento antes de los encabezados
Este error puede aparecer al intentar tener acceso al servicio; por ejemplo, al ir a la dirección URL del servicio en un explorador. 

**Motivo:** el puerto del contenedor no está disponible. Estos son los motivos más comunes: 
* El contenedor todavía está en proceso de compilación e implementación. Esto puede suceder si ejecuta `vsce up` o inicia el depurador y, tras ello, intenta tener acceso al contenedor antes de que se haya implementado correctamente.
* La configuración de los puertos no es coherente en Dockerfile, en el gráfico de Helm y en cualquier otro código de servidor que abra un puerto.

**Pruebe lo siguiente:**
1. Si el contenedor está en proceso de compilación o implementación, puede esperar unos segundos e intentar tener acceso al servicio de nuevo. 
1. Compruebe la configuración de los puertos. Los números de puerto especificados deben ser **idénticos** en todos estos activos:
    * **Dockerfile:** especificado por la instrucción `EXPOSE`.
    * **[Gráfico de Helm:](https://docs.helm.sh)** especificado por los valores `externalPort` e `internalPort` de un servicio (suelen estar en un archivo `values.yml`).
    * Cualquier puerto que se abra en un código de aplicación, por ejemplo, en Node.js: `var server = app.listen(80, function () {...}`.


## <a name="config-file-not-found"></a>No se encuentra el archivo de configuración
Al ejecutar `vsce up`, se muestra el siguiente error: `Config file not found: .../vsce.yaml`.

**Motivo:** `vsce up` debe ejecutarse desde el directorio raíz del código que se quiere ejecutar y, de igual modo, la carpeta del código debe haberse inicializado para ejecutarse con Connected Environment.

**Pruebe lo siguiente:**
1. Cambie el directorio actual a la carpeta raíz que contenga el código del servicio. 
1. Si no tiene un archivo vsce.yaml en la carpeta de código, ejecute `vsce init` para generar activos de Docker, Kubernetes y VSCE.

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>Error que indica que el programa de canalización "vsce" terminó inesperadamente con el código 126
Al iniciar el depurador de VS Code, a veces se produce este error.

**Pruebe lo siguiente:**
1. Cierre y vuelva a abrir VS Code.
2. Presione F5 otra vez.


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>Error de depuración que indica que el tipo de depuración configurado "coreclr" no se admite
Al ejecutar el depurador de VS Code, aparece este error: `Configured debug type 'coreclr' is not supported.`

**Motivo:** no tiene la extensión de VS Code para Connected Environment instalada en el equipo de desarrollo.

**Pruebe lo siguiente:** instale la [extensión de VS Code para Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>Azure Portal no muestra instancias de Connected Environment

**Motivo:** la experiencia de Azure Portal para Connected Environment aún no está lista para la versión preliminar.


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>El tipo o nombre del espacio de nombres "MyLibrary" no se pudo encontrar

**Motivo:** el contexto de compilación está en el nivel de proyecto/servicio de forma predeterminada, de ahí que no se encuentre un proyecto de biblioteca que se está usando.

**Haga lo siguiente:**
1. Modifique el archivo vsce.yaml para establecer el contexto de compilación en el nivel de la solución.
2. Modifique los archivos Dockerfile y Dockerfile.develop para que hagan referencia correctamente a los archivos .csproj relativos al nuevo contexto de compilación.
3. Coloque un archivo .dockerignore junto al archivo .sln y modifique lo que sea necesario.

Encontrará un ejemplo en https://github.com/sgreenmsft/buildcontextsample.

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>Error de autorización de "Microsoft.ConnectedEnvironment/register/action" al crear un entorno
El siguiente error puede aparecer si administra un entorno y está trabajando en una suscripción de Azure en la que carece de acceso de propietario o colaborador.
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**Motivo:** la suscripción a Azure seleccionada no tiene registrado el espacio de nombres Microsoft.ConnectedEnvironment.

**Pruebe lo siguiente:** alguien con acceso de propietario o colaborador a la suscripción de Azure puede ejecutar el siguiente comando de CLI de Azure para registrar manualmente el espacio de nombres Microsoft.ConnectedEnvironment:

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>No parece que VSCE use mi Dockerfile existente para crear un contenedor 

**Motivo:** VSCE se puede configurar para que apunte a un archivo Dockerfile específico del proyecto. Si parece que VSCE no está usando el Dockerfile previsto para generar los contenedores, deberá indicar a VSCE expresamente dónde está. 

**Pruebe lo siguiente:** abra el archivo `vsce.yaml` generado por VSCE en el proyecto. Use la directiva `configurations->develop->build->dockerfile` para que apunte al Dockerfile que quiera usar:

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```