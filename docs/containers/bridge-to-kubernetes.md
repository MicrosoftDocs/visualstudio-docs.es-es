---
title: 'Tutorial: Conexión de máquinas de desarrollo con Bridge to Kubernetes'
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: tutorial
description: Conecte el equipo de desarrollo a un clúster de Kubernetes con Bridge to Kubernetes con Visual Studio.
keywords: Puente a Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, contenedores
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: b8d6c98d2e2146ad57871b74cd2d522ed2b04259
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046123"
---
# <a name="tutorial-use-bridge-to-kubernetes-to-connect-your-clusters-and-your-development-computers"></a>Tutorial: Uso de Bridge to Kubernetes para conectar los clústeres y los equipos de desarrollo

En este tutorial, aprenderá a usar Bridge to Kubernetes para redirigir el tráfico entre el clúster de Kubernetes y el código en ejecución en el equipo de desarrollo. 

También se proporciona un script para implementar una aplicación de ejemplo de gran tamaño con varios microservicios en un clúster de Kubernetes.

Obtenga más información sobre Bridge to Kubernetes con el artículo [Cómo funciona Bridge to Kubernetes](overview-bridge-to-kubernetes.md).

## <a name="prerequisites"></a>Prerrequisitos

- Un clúster de Kubernetes
- [Visual Studio 2019][visual-studio], versión 16.7 Preview 4 o posterior ejecutándose en Windows 10.
- [Extensión Bridge to Kubernetes instalada][btk-extension]

## <a name="about-the-data"></a>Acerca de los datos

En este tutorial se usa Bridge to Kubernetes para desarrollar una versión de microservicio de una aplicación TODO simple en cualquier clúster de Kubernetes. Esta [aplicación de ejemplo TODO][todo-app-github], con Visual Studio, se ha adaptado del código proporcionado por [TodoMVC](http://todomvc.com). 

 Estos pasos deben funcionar con cualquier clúster de Kubernetes. Por tanto, si ya tiene una aplicación que se ejecuta en un clúster de Kubernetes, puede seguir los pasos que se indican a continuación y usar los nombres de los servicios propios.

El ejemplo de aplicación TODO se compone de un front-end y un back-end que proporciona almacenamiento persistente. Este ejemplo extendido agrega un componente de estadísticas y divide la aplicación en varios microservicios, en concreto:

- El front-end llama a la API de base de datos para conservar y actualizar los elementos de TODO.
- El servicio de API de base de datos se basa en una base de datos Mongo para conservar los elementos de TODO.
- El front-end escribe eventos de adición, finalización y eliminación en una cola RabbitMQ.
- Un trabajo de estadísticas recibe eventos de la cola RabbitMQ y actualiza una caché Redis.
- Una API de estadísticas expone las estadísticas almacenadas en caché para que las muestre el front-end.

En total, esta aplicación TODO extendida contiene seis componentes interrelacionados.


## <a name="check-the-cluster"></a>Comprobación del clúster

Abra un símbolo del sistema y compruebe que `kubectl` esté instalado y en la ruta de acceso, que el clúster que quiere usar esté disponible y listo, y establezca el contexto en ese clúster.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

donde {context-name} es el nombre del contexto del clúster que quiere usar para el ejemplo de la aplicación TODO.

## <a name="deploy-the-application"></a>Implementación de la aplicación

Clone el [repositorio de mindaro](https://github.com/Microsoft/mindaro) y abra una ventana de comandos con la carpeta de trabajo actual en *samples/todo-app*.

Cree un espacio de nombres para el ejemplo.

```cmd
kubectl create namespace todo-app
```

A continuación, aplique el manifiesto de implementación:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Se trata de una implementación sencilla que expone el front-end mediante un servicio de tipo `LoadBalancer`. Espere a que se ejecuten todos los pods y a que la dirección IP externa del servicio `frontend` esté disponible.

Si está probando con MiniKube, deberá usar `minikube tunnel` para resolver una dirección IP externa. Si usa AKS u otro proveedor de Kubernetes basado en la nube, se asigna automáticamente una dirección IP externa. Use el siguiente comando para supervisar el servicio `frontend` de forma que espere hasta que esté en funcionamiento:

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Vaya a la aplicación mediante la dirección IP externa y el puerto local (el primer número de la columna de puertos).

```
http://{external-ip}:{local-port}
```

Pruebe la aplicación en ejecución en el explorador. Al agregar, completar y eliminar elementos de la aplicación TODO, tenga en cuenta que la página de estadísticas se actualiza con las métricas esperadas.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Conexión al clúster y depuración de un servicio

Abra *samples\todo-app\database-api\database-api.csproj* en Visual Studio. En el proyecto, seleccione **Bridge to Kubernetes** en el menú desplegable de configuración de inicio, tal y como se muestra a continuación.

![Elección de Puente a Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Haga clic en el botón Inicio junto a *Puente a Kubernetes*. En el cuadro de diálogo **Crear perfil para Puente a Kubernetes**:

- Seleccione el nombre del clúster.
- Seleccione *todo-app* como su espacio de nombres.
- Seleccione *database-api* para el servicio que se va a redirigir.
- Seleccione la misma dirección URL que usó anteriormente para iniciar el explorador, http://{external-ip}:{local-port}.

![Elección del clúster de Puente a Kubernetes](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Elija si quiere ejecutar de forma aislada, lo que significa que otros usuarios que utilicen el clúster no se verán afectados por los cambios. Este modo de aislamiento se consigue enrutando las solicitudes a la copia de cada servicio afectado, pero enrutando el resto de tráfico con normalidad. Puede encontrar más información sobre cómo hacerlo en [Funcionamiento del Puente a Kubernetes][btk-overview-routing].

Haga clic en **OK**. Todo el tráfico del clúster de Kubernetes se redirige para el servicio *database-api* a la versión de la aplicación que se ejecuta en el equipo de desarrollo. Puente a Kubernetes también enruta todo el tráfico saliente desde la aplicación al clúster de Kubernetes.

> [!NOTE]
> Se le pedirá que permita que *EndpointManager* se ejecute con privilegios elevados y modifique el archivo hosts.

El equipo de desarrollo está conectado cuando la barra de estado muestra que está conectado en el servicio `database-api`.

![Equipo de desarrollo conectado](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> En los posteriores, no se le presentará el cuadro de diálogo **Crear perfil para Puente a Kubernetes**. Esta configuración se actualiza en el panel **Depurar** de las propiedades del proyecto.

Una vez que el equipo de desarrollo está conectado, el tráfico comienza a redirigirse a dicho equipo para el servicio que está reemplazando.

> [!NOTE]
> Para editar el perfil de depuración más adelante, por ejemplo, si desea probar con otro servicio de Kubernetes, elija **Depurar** > **Propiedades de depuración** y haga clic en el botón **Cambiar**.

## <a name="set-a-break-point"></a>Establecer un punto de interrupción

Abra MongoHelper.cs y haga clic en algún lugar de la línea 68 del método CreateTask para poner el cursor allí. Para establecer un punto de interrupción, pulse *F9* o seleccione **Depurar** > **Alternar punto de interrupción**.

Navegue hasta la aplicación de ejemplo abriendo la dirección URL pública (la dirección IP externa para el servicio de front-end). Para reanudar el servicio, pulse **F5** o haga clic en **Depurar** > **Continuar**.

Quite el punto de interrupción colocando el cursor en la línea con el punto de interrupción y presionando **F9**.

> [!NOTE]
> De forma predeterminada, al detener la tarea de depuración también se desconecta el equipo de desarrollo del clúster de Kubernetes. Para cambiar este comportamiento, puede cambiar el valor **Disconnect after debugging** (Desconectarse después de la depuración) a `false` en la sección **Kubernetes Debugging Tools** (Herramientas de depuración de Kubernetes) del cuadro de diálogo **Herramientas** > **Opciones**. Después de actualizar esta configuración, el equipo de desarrollo permanecerá conectado cuando detenga e inicie la depuración. Para desconectar el equipo de desarrollo del clúster, haga clic en el botón **Desconectar** de la barra de herramientas.
>
>![Captura de pantalla de las opciones de depuración de Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Configuración adicional

Puente a Kubernetes puede controlar el tráfico de enrutamiento y las variables del entorno de replicación sin ninguna configuración adicional. Si necesita descargar los archivos que se montan en el contenedor del clúster de Kubernetes, como un archivo ConfigMap, puede crear un `KubernetesLocalProcessConfig.yaml` para descargar esos archivos en el equipo de desarrollo. Para más información, consulte el artículo sobre cómo [usar KubernetesLocalProcessConfig.yaml para obtener una configuración adicional con Puente a Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Uso de registro y diagnóstico

Puede encontrar los registros de diagnóstico en el directorio `Bridge to Kubernetes` del directorio *TEMP* del equipo de desarrollo.

## <a name="next-steps"></a>Pasos siguientes

Conozca el funcionamiento del Puente a Kubernetes.

> [!div class="nextstepaction"]
> [Funcionamiento del Puente a Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
