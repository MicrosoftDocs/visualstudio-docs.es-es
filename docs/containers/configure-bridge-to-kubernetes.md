---
title: Uso de KubernetesLocalProcessConfig.yaml para obtener una configuración adicional con Puente a Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Describe las opciones de configuración adicionales para Puente a Kubernetes mediante KubernetesLocalProcessConfig.yaml.
keywords: Puente a Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, AKS, Azure Kubernetes Service, contenedores
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: bd28921b7812689554e1dd707c500434bb021c9c
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845979"
---
# <a name="configure-bridge-to-kubernetes"></a>Configuración del Puente a Kubernetes

El archivo `KubernetesLocalProcessConfig.yaml` le permite replicar variables de entorno y archivos montados disponibles para los pods en el clúster de AKS. Puede especificar las siguientes acciones en un archivo `KubernetesLocalProcessConfig.yaml`:

* Descargue un volumen y establezca la ruta de acceso a ese volumen como una variable de entorno.
* Haga que un servicio que se ejecuta en el clúster esté disponible para los procesos que se ejecutan en el equipo de desarrollo.
* Cree una variable de entorno con un valor constante.

Un archivo `KubernetesLocalProcessConfig.yaml` predeterminado no se crea automáticamente, por lo cual debe crear manualmente el archivo en la raíz del proyecto.

## <a name="download-a-volume"></a>Descargar un volumen

En *env*, especifique un *nombre* y un *valor* para cada volumen que desee descargar. El *nombre* es la variable de entorno que se utilizará en el equipo de desarrollo. El *valor* es el nombre del volumen y una ruta de acceso en el equipo de desarrollo. El valor de *value* toma la forma *$ (volumeMounts:VOLUME_NAME)/PATH/TO/FILES*.

Por ejemplo:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

En el ejemplo anterior se descarga el volumen de *listas de permitidos* del contenedor y se establece esa ubicación más la ruta de acceso en la variable de entorno *ALLOW_LIST_PATH*. El comportamiento predeterminado es descargar los archivos en la ruta de acceso especificada en un directorio temporal del equipo de desarrollo. En el ejemplo anterior, *ALLOW_LIST_PATH* se establece en `/TEMPORARY_DIR/allow-list`. 

> [!NOTE]
> Al descargar un volumen se descargará todo el contenido de dicho volumen independientemente de la ruta de acceso establecida. La ruta de acceso solo se utiliza con el fin de establecer la variable de entorno para su uso en el equipo de desarrollo. Agregar */allow-list* o */path/to/files* al final del token no afecta realmente al lugar donde se conserva el volumen. La variable de entorno es simplemente una comodidad en caso de que la aplicación necesite una referencia a un archivo específico dentro de ese volumen.

También tiene la opción de especificar una ubicación para descargar el montaje del volumen en el equipo de desarrollo en lugar de usar un directorio temporal. En *volumeMounts*, especifique un *nombre* y *localPath* para cada ubicación específica. El *nombre* es el nombre del volumen que desea comparar y *localPath* es la ruta de acceso absoluta del equipo de desarrollo. Por ejemplo:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

En el ejemplo anterior se usa la entrada en *env* para descargar un volumen que coincida con *default-token-\** , como *default-token-1111* o *default-token-1234-5678-90abcdef*. En los casos en los que varios volúmenes coinciden, se usa el primer volumen coincidente. Todos los archivos se descargan en `/var/run/secrets/kubernetes.io/serviceaccount`, en el equipo de desarrollo, mediante la entrada de *volumeMounts*. La variable de entorno *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* se establece en `/var/run/secrets/kubernetes.io/serviceaccount`.

## <a name="make-a-service-available"></a>Hacer que un servicio esté disponible

En *env*, especifique un *nombre* y un *valor* para cada servicio que desee ofrecer en el equipo de desarrollo. El *nombre* es la variable de entorno que se utilizará en el equipo de desarrollo. El *valor* es el nombre del servicio del clúster y una ruta de acceso. El valor de *value* toma la forma *$(services:SERVICE_NAME)/PATH*.

Por ejemplo:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

En el ejemplo anterior, se tiene acceso al servicio *myapp1* en el equipo de desarrollo, y la variable de entorno *MYAPP1_SERVICE_HOST* se establece en la dirección IP local del servicio *myapp1* con la ruta de acceso `/api/v1` (es decir, `127.1.1.4/api/v1`). Se puede obtener acceso al servicio *myapp1* mediante la variable de entorno, *myapp1* o *myapp1.svc.cluster.local*.

> [!NOTE]
> Al hacer que un servicio esté disponible en el equipo de desarrollo, todo el servicio estará disponible independientemente de la ruta de acceso establecida. La ruta de acceso solo se utiliza con el fin de establecer la variable de entorno para su uso en el equipo de desarrollo.
También puede hacer que un servicio de un espacio de nombres de Kubernetes específico esté disponible mediante *$(services:SERVICE_NAME.NAMESPACE_NAME)* . Por ejemplo:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

En el ejemplo anterior, se obtiene acceso a *myapp2* del espacio de nombres *mynamespace* en el equipo de desarrollo y se establece la variable de entorno *MYAPP2_SERVICE_HOST* en la dirección IP local de *myapp2* del espacio de nombres *mynamespace*.

## <a name="create-an-environment-variable-with-a-constant-value"></a>Crear una variable de entorno con un valor constante

En *env*, especifique un *nombre* y un *valor* para cada variable de entorno que desee crear en el equipo de desarrollo. El *nombre* es la variable de entorno que se utilizará en el equipo de desarrollo y *value* es el valor. Por ejemplo:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

En el ejemplo anterior se crea una variable de entorno denominada *DEBUG_MODE* con un valor de *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>KubernetesLocalProcessConfig.yaml de ejemplo

Este es un ejemplo de un archivo `KubernetesLocalProcessConfig.yaml` completo:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Pasos siguientes

Para empezar a usar Puente a Kubernetes para conectarse al equipo de desarrollo local en el clúster, consulte [Uso de Bridge to Kubernetes con Visual Studio Code][bridge-to-kubernetes-vs-code] y [Uso del Puente a Kubernetes con Visual Studio][bridge-to-kubernetes-vs].

[bridge-to-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/bridge-to-kubernetes
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
