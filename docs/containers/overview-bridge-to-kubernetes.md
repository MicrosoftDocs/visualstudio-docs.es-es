---
title: Funcionamiento del Puente a Kubernetes
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: Describe los procesos para usar Puente a Kubernetes para conectar el equipo de desarrollo con el clúster de Kubernetes.
keywords: Puente a Kubernetes, Docker, Kubernetes, Azure, contenedores
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 1709785c63bd4fbcd702fbcacfe59dddcb71d1b3
ms.sourcegitcommit: 0135fc6ffa38995cc9e6ab05fa265758890d2e15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2021
ms.locfileid: "107526156"
---
# <a name="how-bridge-to-kubernetes-works"></a>Funcionamiento del Puente a Kubernetes

Puente a Kubernetes le permite ejecutar y depurar el código en el equipo de desarrollo mientras sigue conectado al clúster de Kubernetes con el resto de aplicaciones o servicios. Por ejemplo, si tiene una arquitectura de microservicios de gran tamaño con muchos servicios y bases de datos interdependientes, la replicación de esas dependencias en el equipo de desarrollo puede resultar difícil. Además, el proceso de compilación e implementación del código en el clúster de Kubernetes para cada cambio de código durante el desarrollo del bucle interno puede resultar lento y difícil de usar con un depurador, además de llevarle mucho tiempo.

Puente a Kubernetes evita tener que compilar e implementar el código en el clúster creando en su lugar una conexión directa entre el equipo de desarrollo y el clúster. La conexión del equipo de desarrollo al clúster durante la depuración le permite probar y desarrollar rápidamente el servicio en el contexto de la aplicación completa sin necesidad de crear ninguna configuración de Docker o Kubernetes.

Puente a Kubernetes redirige el tráfico entre el clúster de Kubernetes conectado y el equipo de desarrollo. Esta redirección del tráfico permite que el código del equipo de desarrollo y los servicios que se ejecutan en el clúster de Kubernetes se comuniquen como si estuvieran en el mismo clúster de Kubernetes. Puente a Kubernetes también proporciona una manera de replicar variables de entorno y volúmenes montados disponibles para pods en el clúster de Kubernetes en el equipo de desarrollo. Proporcionar acceso a las variables de entorno y a los volúmenes montados en el equipo de desarrollo le permite trabajar rápidamente en el código sin tener que replicar dichas dependencias manualmente.

> [!WARNING]
> Puente a Kubernetes está pensado únicamente para su uso en escenarios de desarrollo y pruebas. No está pensado ni se admite para su uso con clústeres de producción o servicios en vivo que se utilizan de forma activa.

Puede encontrar información sobre las características admitidas actualmente y un plan de desarrollo futuro para Bridge to Kubernetes en [Plan de desarrollo de Bridge to Kubernetes](https://github.com/microsoft/mindaro/projects/1).

## <a name="using-bridge-to-kubernetes"></a>Uso de Puente a Kubernetes

Para usar Puente a Kubernetes en Visual Studio, necesita la versión preliminar 4 de [Visual Studio 2019][visual-studio], versión 16.7, o una que se ejecute en Windows 10 con la carga de trabajo *ASP.NET y desarrollo web* y la [extensión Puente a Kubernetes][btk-extension] instaladas. Al usar Puente a Kubernetes para establecer una conexión con el clúster de Kubernetes, tiene la opción de redirigir todo el tráfico hacia y desde un pod nuevo o existente en el clúster al equipo de desarrollo.

> [!NOTE]
> Al usar Puente a Kubernetes, se le pedirá el nombre del servicio que desea redirigir al equipo de desarrollo. Esta opción es una forma cómoda de identificar un POD para el redireccionamiento. Todo el redireccionamiento entre el clúster de Kubernetes y el equipo de desarrollo es para un pod.

Cuando Puente a Kubernetes establece una conexión con el clúster, hace lo siguiente:

* Le pide que configure el servicio para reemplazar en el clúster, el puerto del equipo de desarrollo que se va a usar para el código y la tarea de inicio del código como una acción única.
* Reemplaza el contenedor del pod en el clúster por un contenedor de agente remoto que redirige el tráfico al equipo de desarrollo.
* Ejecuta [kubectl port-forward][kubectl-port-forward] en el equipo de desarrollo para reenviar el tráfico desde el equipo de desarrollo al agente remoto que se ejecuta en el clúster.
* Recopila información de entorno del clúster mediante el agente remoto. Esta información de entorno incluye variables de entorno, servicios visibles, montajes de volúmenes y montajes de secretos.
* Configura el entorno en Visual Studio de modo que el servicio del equipo de desarrollo pueda acceder a las mismas variables como si se estuviera ejecutando en el clúster.
* Actualiza el archivo de hosts para asignar servicios en el clúster a direcciones IP locales en el equipo de desarrollo. Estas entradas de archivo de host permiten que el código que se ejecuta en el equipo de desarrollo realice solicitudes a otros servicios que se ejecutan en el clúster. Para actualizar el archivo hosts, Puente a Kubernetes solicitará acceso de administrador en el equipo de desarrollo al conectarse al clúster.
* Comienza a ejecutar y depurar el código en el equipo de desarrollo. Si es necesario, Puente a Kubernetes liberará los puertos necesarios en el equipo de desarrollo mediante la detención de los servicios o procesos que usan actualmente esos puertos.

Después de establecer una conexión con el clúster, puede ejecutar y depurar el código de forma nativa en el equipo, sin contenedores, y el código puede interactuar directamente con el resto del clúster. Cualquier tráfico que reciba el agente remoto se redirige al puerto local especificado durante la conexión para que el código que se ejecuta de forma nativa pueda aceptar y procesar ese tráfico. Las variables de entorno, los volúmenes y los secretos del clúster se ponen a disposición del código que se ejecuta en el equipo de desarrollo. Además, debido a las entradas del archivo hosts y el reenvío de puertos que Puente a Kubernetes agregó al equipo del desarrollador, el código puede enviar tráfico de red a los servicios que se ejecutan en el clúster mediante los nombres de servicio del clúster, y ese tráfico se reenvía a los servicios que se ejecutan en el clúster. El tráfico se enruta entre el equipo de desarrollo y el clúster todo el tiempo que está conectado.

Además, Puente a Kubernetes proporciona una manera de replicar variables de entorno y archivos montados disponibles para pods en el clúster en el equipo de desarrollo mediante el archivo `KubernetesLocalProcessConfig.yaml`. También puede usar este archivo para crear nuevas variables de entorno y montajes de volúmenes.

> [!NOTE]
> Durante toda la conexión al clúster (más unos 15 minutos adicionales), Puente a Kubernetes ejecuta un proceso llamado *EndpointManager* con permisos de administrador en el equipo local.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Configuración adicional con KubernetesLocalProcessConfig.yaml

El archivo `KubernetesLocalProcessConfig.yaml` le permite replicar variables de entorno y archivos montados disponibles para los pods en el clúster. Al usar Visual Studio para el desarrollo de Bridge to Kubernetes, el archivo KubernetesLocalConfig.yaml se debe encontrar en el mismo directorio que el archivo del proyecto para el servicio que se redirige. Para más información sobre las opciones de configuración adicionales, consulte [Configuración de Puente a Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Uso de funciones de enrutamiento para desarrollar de forma aislada

De forma predeterminada, Puente a Kubernetes redirige todo el tráfico para un servicio al equipo de desarrollo. También tiene la opción de usar funciones de enrutamiento para redirigir únicamente las solicitudes a un servicio que se originen en un subdominio del equipo de desarrollo. Estas funciones de enrutamiento permiten usar Puente a Kubernetes para desarrollar de forma aislada y evitar interrumpir el resto del tráfico del clúster.

En la siguiente animación se muestran dos desarrolladores que trabajan en el mismo clúster de forma aislada:

![GIF animado que ilustra el aislamiento](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Cuando se habilita el trabajo de forma aislada, además de conectarse al clúster de Kubernetes, Puente a Kubernetes hace lo siguiente:

* Comprueba que el clúster de Kubernetes no tiene habilitado Azure Dev Spaces.
* Replica el servicio seleccionado en el clúster en el mismo espacio de nombres y agrega una etiqueta *routing.visualstudio.io/route-from=SERVICE_NAME* y una anotación *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME*.
* Configura e inicia el administrador de enrutamiento en el mismo espacio de nombres en el clúster de Kubernetes. El administrador de enrutamiento usa un selector de etiquetas para buscar la etiqueta *routing.visualstudio.io/route-from=SERVICE_NAME* y la anotación *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* al configurar el enrutamiento en el espacio de nombres.

Si Puente a Kubernetes detecta que Azure Dev Spaces está habilitado en el clúster de Kubernetes, se le pedirá que deshabilite Azure Dev Spaces para poder usar Puente a Kubernetes.

El administrador de enrutamiento hace lo siguiente cuando se inicia:

* Duplica todas las entradas (incluidas las del equilibrador de carga) que se encuentran en el espacio de nombres mediante el valor *GENERATED_NAME* para el subdominio.
* Crea un pod de envío para cada servicio asociado a las entradas duplicadas con el subdominio *GENERATED_NAME*.
* Crea un pod de envío adicional para el servicio en el que se trabaja de forma aislada. Esto permite que las solicitudes con el subdominio se enruten al equipo de desarrollo.
* Configura reglas de enrutamiento para que cada pod de envío controle el enrutamiento de servicios con el subdominio.

En el diagrama siguiente se muestra un clúster de Kubernetes antes de que Puente a Kubernetes se conecte al clúster:

![Diagrama del clúster sin Puente a Kubernetes](media/bridge-to-kubernetes/kubr-cluster.svg)

En el diagrama siguiente se muestra el mismo clúster con Puente a Kubernetes habilitado en modo de aislamiento. Aquí puede ver el servicio duplicado y los pods de envío que admiten el enrutamiento en aislamiento.

![Diagrama del clúster con Puente a Kubernetes habilitado](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

Cuando se recibe en el clúster una solicitud con el subdominio *GENERATED_NAME*, se agrega un encabezado *kubernetes-route-as=GENERATED_NAME* a la solicitud. Los pods de envío controlan el enrutamiento de la solicitud al servicio adecuado en el clúster. Si la solicitud se enruta al servicio en el que se trabaja de forma aislada, el agente remoto redirige esa solicitud al equipo de desarrollo.

Cuando se recibe en el clúster una solicitud sin el subdominio *GENERATED_NAME*, no se agrega ningún encabezado a la solicitud. Los pods de envío controlan el enrutamiento de la solicitud al servicio adecuado en el clúster. Si la solicitud se enruta al servicio que se va a reemplazar, se enrutará al servicio original en lugar de al agente remoto.

> [!IMPORTANT]
> Cada servicio del clúster debe reenviar el encabezado *kubernetes-route-as=GENERATED_NAME* al realizar solicitudes adicionales. Por ejemplo, cuando *serviceA* recibe una solicitud, realiza una solicitud a *serviceB* antes de devolver una respuesta. En este ejemplo, *serviceA* tiene que reenviar el encabezado *kubernetes-route-as=GENERATED_NAME* de su solicitud a *serviceB*. Algunos lenguajes, como [ASP.NET][asp-net-header], pueden tener métodos para controlar la propagación de encabezados.

Cuando se desconecta del clúster, de forma predeterminada, Puente a Kubernetes quitará todos los pods de envío y el servicio duplicado.

> [!NOTE]
> La implementación y el servicio del administrador de enrutamiento seguirán ejecutándose en el espacio de nombres. Para quitar la implementación y el servicio, ejecute los siguientes comandos para el espacio de nombres.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnósticos y registro

Al usar Puente a Kubernetes para conectarse al clúster, los registros de diagnóstico del clúster se registran en el directorio *TEMP* del equipo de desarrollo en la carpeta *Puente a Kubernetes*.

## <a name="rbac-authorization"></a>Autorización de RBAC

Kubernetes proporciona control de acceso basado en rol (RBAC) para administrar permisos de usuarios y grupos. Para información, consulte la [documentación de Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/). Puede establecer los permisos de un clúster habilitado para RBAC mediante la creación de un archivo YAML y el uso de `kubectl` para aplicarlo al clúster. 

Para establecer permisos en el clúster, cree o modifique un archivo YAML (por ejemplo, *permissions.yml*) de la manera siguiente, usando su propio espacio de nombres para `<namespace>` y los sujetos (usuarios y grupos) que necesitan acceso.

```yml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: bridgetokubernetes-<namespace>
  namespace: development
subjects:
  - kind: User
    name: jane.w6wn8.k8s.ginger.eu-central-1.aws.gigantic.io
    apiGroup: rbac.authorization.k8s.io
  - kind: Group
    name: dev-admin
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: admin
  apiGroup: rbac.authorization.k8s.io
```

Aplique los permisos mediante el comando:

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>Limitaciones

Puente a Kubernetes tiene las siguientes limitaciones:

* Un pod solo puede tener un único contenedor en ejecución en ese pod para que el Puente a Kubernetes se conecte correctamente.
* Actualmente, los pods de Bridge to Kubernetes deben ser contenedores de Linux. No se admiten los contenedores de Windows.
* Puente a Kubernetes necesita permisos elevados para ejecutarse en el equipo de desarrollo con el fin de editar el archivo hosts.
* Puente a Kubernetes no se puede usar en clústeres que tengan habilitado Azure Dev Spaces.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Puente a Kubernetes y clústeres con Azure Dev Spaces habilitado

No se puede usar Puente a Kubernetes en un clúster que tenga habilitado Azure Dev Spaces. Si quiere usar Puente a Kubernetes en un clúster con Azure Dev Spaces habilitado, debe deshabilitar Azure Dev Spaces antes de conectarse al clúster.

## <a name="next-steps"></a>Pasos siguientes

Para empezar a usar Puente a Kubernetes para conectarse al equipo de desarrollo local en el clúster, consulte [Uso de Puente a Kubernetes](bridge-to-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md
