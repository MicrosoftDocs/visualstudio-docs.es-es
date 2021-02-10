---
title: Uso del Puente a Kubernetes con Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Más información sobre cómo usar Puente a Kubernetes con Visual Studio para conectar el equipo de desarrollo a un clúster de Kubernetes
keywords: Puente a Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, contenedores
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: 23d060489a13aa8e02316e253d9367e9e3372bbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859637"
---
# <a name="use-bridge-to-kubernetes"></a>Uso de Puente a Kubernetes

Puede usar Puente a Kubernetes para redirigir el tráfico entre el clúster de Kubernetes y el código en ejecución en el equipo de desarrollo. También se proporciona un script para implementar una aplicación de ejemplo de gran tamaño con varios microservicios en un clúster de Kubernetes.

## <a name="before-you-begin"></a>Antes de empezar

En esta guía se usa la [aplicación de ejemplo Bike Sharing][bike-sharing-github] para mostrar la conexión del equipo de desarrollo a un clúster de Kubernetes. Si ya tiene una aplicación que se ejecuta en un clúster de Kubernetes, puede seguir los pasos que se indican a continuación y usar los nombres de sus servicios.

### <a name="prerequisites"></a>Requisitos previos

* Suscripción a Azure. Si no tiene una suscripción a Azure, puede crear una [cuenta gratuita](https://azure.microsoft.com/free).
* [La CLI de Azure instalada][azure-cli].
* Versión preliminar 4 de [Visual Studio 2019][visual-studio], versión 16.7, o una posterior que se ejecute en Windows 10 con la carga de trabajo *Desarrollo de Azure* instalada.
* [Extensión Puente a Kubernetes instalada][btk-extension].

Además, para las aplicaciones de consola .NET, instale paquete NuGet *Microsoft.VisualStudio.Azure.Kubernetes.Tools.Targets*.

## <a name="create-a-kubernetes-cluster"></a>Creación de un clúster de Kubernetes

Cree un clúster de AKS en una [región admitida][supported-regions]. Los siguientes comandos permiten crear un grupo de recursos llamado *MyResourceGroup* y un clúster de AKS denominado *MyAKS*.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Instale la aplicación de ejemplo.

Instale la aplicación de ejemplo en el clúster con el script proporcionado. Puede ejecutar este script con [Azure Cloud Shell][azure-cloud-shell].

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Navegue hasta la aplicación de ejemplo en la que se ejecuta el clúster. Para ello, abra su URL pública, que se muestra en la salida del script de instalación.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

En el ejemplo anterior, la URL pública es `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Conexión al clúster y depuración de un servicio

En el equipo de desarrollo, descargue y configure la CLI de Kubernetes para conectarse al clúster de Kubernetes mediante [az aks get-credentials][az-aks-get-credentials].

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

En el repositorio de la [aplicación de ejemplo Bike Sharing][bike-sharing-github] de GitHub, utilice la lista desplegable del botón verde **Code** (Código) y elija **Abrir en Visual Studio** para clonar el repositorio localmente y abrir la carpeta en Visual Studio. Después, use **Archivo** > **Abrir proyecto** para abrir el proyecto **app.csproj** en la carpeta *samples/BikeSharingApp/ReservationEngine*.

En el proyecto, seleccione **Puente a Kubernetes** en el menú desplegable de configuración de inicio, tal y como se muestra a continuación.

![Elección de Puente a Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Haga clic en el botón Inicio junto a *Puente a Kubernetes*. En el cuadro de diálogo **Crear perfil para Puente a Kubernetes**:

* Seleccione su suscripción.
* Seleccione *MyAKS* para el clúster.
* Seleccione *bikeapp* como su espacio de nombres.
* Seleccione *reservationengine* para el servicio que se va a redirigir.
* Seleccione *app* para el perfil de inicio.
* Seleccione `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` para la dirección URL que debe iniciar el explorador.

![Elección del clúster de Puente a Kubernetes](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Solo puede redirigir servicios que tengan un único pod.

Elija si quiere ejecutar de forma aislada, lo que significa que otros usuarios que utilicen el clúster no se verán afectados por los cambios. Este modo de aislamiento se consigue enrutando las solicitudes a la copia de cada servicio afectado, pero enrutando el resto de tráfico con normalidad. Puede encontrar más información sobre cómo hacerlo en [Funcionamiento del Puente a Kubernetes][btk-overview-routing].

Haga clic en **Guardar e iniciar la depuración**.

Todo el tráfico del clúster de Kubernetes se redirige para el servicio *reservationengine* a la versión de la aplicación que se ejecuta en el equipo de desarrollo. Puente a Kubernetes también enruta todo el tráfico saliente desde la aplicación al clúster de Kubernetes.

> [!NOTE]
> Se le pedirá que permita que *EndpointManager* se ejecute con privilegios elevados y modifique el archivo hosts.

El equipo de desarrollo está conectado cuando la barra de estado muestra que está conectado en el servicio `reservationengine`.

![Equipo de desarrollo conectado](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> En los posteriores, no se le presentará el cuadro de diálogo **Crear perfil para Puente a Kubernetes**. Esta configuración se actualiza en el panel **Depurar** de las propiedades del proyecto.

Una vez que el equipo de desarrollo está conectado, el tráfico comienza a redirigirse a dicho equipo para el servicio que está reemplazando.

## <a name="set-a-break-point"></a>Establecer un punto de interrupción

Abra [BikesHelper.cs][bikeshelper-cs-breakpoint] y haga clic en cualquier lugar de la línea 26 para colocar ahí el cursor. Para establecer un punto de interrupción, pulse *F9* o seleccione **Depurar** > **Alternar punto de interrupción**.

Abra la dirección URL pública para navegar a la aplicación de ejemplo. Seleccione **Aurelia Briggs (customer)** (Aurelia Briggs [cliente]) como usuario y, después, seleccione una bicicleta para alquilar. Elija **Rent Bike** (Alquilar bicicleta). Vuelva a Visual Studio y observe que la línea 26 está resaltada. El punto de interrupción que estableció puso en pausa el servicio en la línea 26. Para reanudar el servicio, pulse **F5** o haga clic en **Depurar** > **Continuar**. Vuelva al explorador y verifique que la página muestra que ha alquilado la bicicleta.

Quite el punto de interrupción colocando el cursor en la línea 26 en `BikesHelper.cs` y pulsando **F9**.

> [!NOTE]
> De forma predeterminada, al detener la tarea de depuración también se desconecta el equipo de desarrollo del clúster de Kubernetes. Para cambiar este comportamiento, puede cambiar el valor **Disconnect after debugging** (Desconectarse después de la depuración) a `false` en la sección **Kubernetes Debugging Tools** (Herramientas de depuración de Kubernetes) de las opciones de depuración. Después de actualizar esta configuración, el equipo de desarrollo permanecerá conectado cuando detenga e inicie la depuración. Para desconectar el equipo de desarrollo del clúster, haga clic en el botón **Desconectar** de la barra de herramientas.

## <a name="additional-configuration"></a>Configuración adicional

Puente a Kubernetes puede controlar el tráfico de enrutamiento y las variables del entorno de replicación sin ninguna configuración adicional. Si necesita descargar los archivos que se montan en el contenedor del clúster de Kubernetes, como un archivo ConfigMap, puede crear un `KubernetesLocalProcessConfig.yaml` para descargar esos archivos en el equipo de desarrollo. Para más información, consulte el artículo sobre cómo [usar KubernetesLocalProcessConfig.yaml para obtener una configuración adicional con Puente a Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Uso de registro y diagnóstico

Puede encontrar los registros de diagnóstico en el directorio `Bridge to Kubernetes` del directorio *TEMP* del equipo de desarrollo. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Eliminación de la aplicación de ejemplo del clúster

Use el script proporcionado para eliminar aplicación de ejemplo del clúster.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Pasos siguientes

Conozca el funcionamiento del Puente a Kubernetes.

> [!div class="nextstepaction"]
> [Funcionamiento del Puente a Kubernetes](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation