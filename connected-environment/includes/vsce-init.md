---
ms.topic: include
ms.openlocfilehash: 394e31bf0660557c1eba571006cacf213263c07e
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031077"
---
## <a name="initialize-code-for-docker-and-kubernetes-development"></a>Inicializar código para el desarrollo de Docker y Kubernetes
Por ahora, tenemos una aplicación web básica que se puede ejecutar localmente. Ahora incluiremos la aplicación en un contenedor; para ello, crearemos activos que definan el contenedor de la aplicación y cómo se implementará en Kubernetes. Esto es muy fácil de hacer con Connected Environment: 

1. Inicie VS Code y abra la carpeta `webfrontend`. (Puede omitir los mensajes predeterminados para agregar recursos de depuración o restaurar el proyecto).
1. Abra el terminal integrado en VS Code (a través del menú **Ver | Terminal integrado**).
1. Ejecute este comando (asegúrese de que **webfrontend** es la carpeta actual):

```cmd
vsce init --public
```

El comando ```init``` de la CLI de Connected Environment genera activos de Docker y de Kubernetes con la configuración predeterminada:
* `./Dockerfile` describe la imagen del contenedor de la aplicación y cómo el código fuente se compila y se ejecuta dentro de dicho contenedor.
* Un [gráfico de Helm](https://docs.helm.sh) en `./charts/webfrontend` describe cómo implementar el contenedor en Kubernetes.

Por ahora no es necesario entender todo el contenido de estos archivos. En cambio, sí merece la pena destacar que **se pueden usar los mismos activos de configuración como código de Kubernetes y Docker durante el desarrollo y hasta la producción, lo que proporciona una mejor coherencia entre entornos distintos**.
 
También se genera un archivo denominado `./vsce.yaml` con el comando `init`; se trata del archivo de configuración de Connected Environment. Complementa los artefactos de Docker y Kubernetes con más opciones de configuración que ofrecen una experiencia de desarrollo iterativo de Azure. Por ejemplo, el gráfico de Helm predeterminado no expone ningún punto de conexión público. A veces, no obstante, resulta útil abrir temporalmente un punto de conexión público durante el desarrollo para poder probar el código en un dispositivo móvil o una dirección URL del webhook. Un archivo vsce.yaml creado con `init --public` invalida los parámetros predeterminados de Helm para exponer un punto de conexión público solo durante la fase de desarrollo.
