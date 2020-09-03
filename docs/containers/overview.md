---
title: Herramientas de contenedor de Visual Studio en Windows
description: Conozca las herramientas disponibles en Visual Studio para trabajar con Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916566"
---
# <a name="container-tools-in-visual-studio"></a>Herramientas de contenedor en Visual Studio

Las herramientas incluidas en Visual Studio para el desarrollo con contenedores son fáciles de usar y simplifican en gran medida la compilación, depuración e implementación de aplicaciones en contenedores. Puede trabajar con un contenedor en un único proyecto o usar la orquestación de contenedores con Docker Compose, Service Fabric o Kubernetes para trabajar con varios servicios en contenedores.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Requisitos previos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* Para publicar en Azure Container Registry, una suscripción de Azure. [Regístrese para obtener una evaluación gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Compatibilidad con Docker en Visual Studio

La compatibilidad con Docker está disponible para proyectos ASP.NET, proyectos ASP.NET Core y proyectos de consola de .NET Core y .NET Framework.

La compatibilidad con Docker en Visual Studio ha cambiado a lo largo de una serie de versiones en respuesta a las necesidades del cliente. Hay dos niveles de compatibilidad con Docker que puede agregar a un proyecto, y las opciones admitidas varían según el tipo de proyecto y la versión de Visual Studio. Con algunos tipos de proyectos admitidos, si simplemente quiere un contenedor para un único proyecto, sin usar la orquestación, puede hacerlo si agrega compatibilidad con Docker.  El siguiente nivel es la compatibilidad con la orquestación de contenedores, que agrega los archivos de compatibilidad adecuados para el orquestador determinado que elija.  

Con Visual Studio 2017, puede usar Docker Compose y Service Fabric como servicios de orquestación de contenedores.  También puede usar Kubernetes si instala [Visual Studio Tools para Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).

> [!NOTE]
> Si usa una versión de Visual Studio 2017 anterior a la 15.8 o bien utiliza la plantilla de proyecto de .NET Framework (no .NET Core), al agregar compatibilidad con Docker se agrega automáticamente compatibilidad con la orquestación con Docker Compose. La compatibilidad con la orquestación de contenedores, mediante Docker Compose, se agrega automáticamente en las versiones de Visual Studio 2017 15.0 a 15.7 y para los proyectos de .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Requisitos previos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* [Herramientas de desarrollo de .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) para el desarrollo con .NET Core.
* Para publicar en Azure Container Registry, una suscripción de Azure. [Regístrese para obtener una evaluación gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Compatibilidad con Docker en Visual Studio

La compatibilidad con Docker está disponible para proyectos ASP.NET, proyectos ASP.NET Core y proyectos de consola de .NET Core y .NET Framework.

La compatibilidad con Docker en Visual Studio ha cambiado a lo largo de una serie de versiones en respuesta a las necesidades del cliente. Hay dos niveles de compatibilidad con Docker que puede agregar a un proyecto, y las opciones admitidas varían según el tipo de proyecto y la versión de Visual Studio. Con algunos tipos de proyectos admitidos, si simplemente quiere un contenedor para un único proyecto, sin usar la orquestación, puede hacerlo si agrega compatibilidad con Docker.  El siguiente nivel es la compatibilidad con la orquestación de contenedores, que agrega los archivos de compatibilidad adecuados para el orquestador determinado que elija.  

Con Visual Studio 2019, puede usar Docker Compose, Kubernetes y Service Fabric como servicios de orquestación de contenedores.

> [!NOTE]
> Si va a usar la plantilla completa del proyecto de consola de .NET Framework, la opción admitida es **Agregar compatibilidad con el orquestador de contenedores** después de la creación del proyecto, con opciones para usar Service Fabric o Docker Compose. La adición de compatibilidad durante la creación del proyecto y la **adición de compatibilidad con Docker** para un único proyecto sin orquestación no son opciones disponibles.

Las versiones 16.4 y posteriores de Visual Studio 2019 incluyen la ventana **Contenedores**, en la que puede ver los contenedores en ejecución, examinar las imágenes disponibles, ver las variables de entorno, los registros y las asignaciones de puertos, inspeccionar el sistema de archivos, adjuntar un depurador o abrir una ventana de terminal dentro del entorno de un contenedor. Vea [Visualización y diagnóstico de contenedores e imágenes en Visual Studio](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Adición de compatibilidad con Docker

Puede habilitar la compatibilidad con Docker durante la creación del proyecto si selecciona **Enable Docker Support** (Habilitar la compatibilidad con Docker) al crear un proyecto, como se muestra en la captura de pantalla siguiente:

::: moniker range="vs-2017"
![Habilitación de la compatibilidad con Docker para una nueva aplicación web de ASP.NET Core en Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Habilitación de la compatibilidad con Docker para una nueva aplicación web de ASP.NET Core en Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Para los proyectos de .NET Framework (no incluye .NET Core), solo están disponibles los contenedores de Windows.

Puede agregar compatibilidad con Docker a un proyecto existente si selecciona **Agregar** > **Compatibilidad con Docker** en el **Explorador de soluciones**. Los comandos **Agregar > Compatibilidad con Docker** y **Agregar > Compatibilidad con el orquestador de contenedores** se encuentran en el menú contextual del nodo de proyecto de un proyecto de ASP.NET Core en el **Explorador de soluciones**, como se muestra en la captura de pantalla siguiente:

![Opción de menú Agregar compatibilidad con Docker en Visual Studio](./media/overview/add-docker-support-menu.png)

Al agregar o habilitar la compatibilidad con Docker, Visual Studio agrega lo siguiente al proyecto:

- un archivo *Dockerfile*
- un archivo .dockerignore
- una referencia de paquete NuGet a Microsoft.VisualStudio.Azure.Containers.Tools.Targets

::: moniker range=">=vs-2019"
Después de agregar la compatibilidad con Docker, la solución tiene este aspecto:

![Captura de pantalla del Explorador de soluciones con Dockerfile y el archivo .dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Al habilitar la compatibilidad con Docker durante la creación de un proyecto de ASP.NET (.NET Framework, no un proyecto de .NET Core) como se muestra en la siguiente captura de pantalla, también se agrega compatibilidad con la orquestación de contenedores.

![Habilitación de la compatibilidad con Docker Compose para un proyecto de ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Compatibilidad con Docker Compose

Cuando quiera crear una solución de varios contenedores mediante Docker Compose, agregue a sus proyectos compatibilidad con la orquestación de contenedores. De esta manera podrá ejecutar y depurar un grupo de contenedores (una solución completa o un grupo de proyectos) al mismo tiempo si se definen en el mismo archivo *docker-compose.yml*.

Para agregar compatibilidad con la orquestación de contenedores mediante Docker Compose, haga clic con el botón derecho en la solución o el nodo del proyecto en el **Explorador de soluciones** y elija **Agregar > Compatibilidad con la orquestación de contenedores**. A continuación, elija **Docker Compose** para administrar los contenedores.

Después de agregar al proyecto compatibilidad con la orquestación de contenedores, verá que se agrega un archivo *Dockerfile* al proyecto (si no había ya uno) y una carpeta **docker-compose** a la solución en el **Explorador de soluciones**, tal y como se muestra aquí:

![Archivos de Docker en el Explorador de soluciones en Visual Studio](media/overview/docker-support-solution-explorer.png)

Si *docker-compose.yml* ya existe, Visual Studio le agrega simplemente las líneas de código de configuración necesarias.

Repita el proceso con los otros proyectos que quiera controlar mediante Docker Compose.

## <a name="kubernetes-support"></a>Soporte técnico de Kubernetes

::: moniker range="vs-2017"
Para agregar compatibilidad con Kubernetes, instale [Visual Studio Tools para Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).
::: moniker-end

Con la compatibilidad con Kubernetes, puede habilitar una conexión entre su proyecto local y un clúster de Kubernetes que se ejecuta en [Azure Kubernetes Service (AKS)](/azure/aks) y, por tanto, modificar y depurar los servicios que se ejecutan en AKS con Visual Studio.  Este servicio se proporciona mediante [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). Azure Dev Spaces también le permite configurar ramas distintas de servicios de Kubernetes llamadas *dev spaces* para fines de desarrollo, de esta manera puede aislar de forma eficaz servicios de producción de las versiones que se usan para desarrollo y mantener las distintas modificaciones claramente separadas unas de otras.

Para agregar a sus proyectos compatibilidad con Kubernetes, elija **Kubernetes/Helm** al agregar compatibilidad con la orquestación de contenedores. Se agregan varios archivos al proyecto, como *azds.yaml*, que configura Azure Dev Spaces, y gráficos de Helm, que describen la estructura de los servicios de Kubernetes.

## <a name="service-fabric-support"></a>Compatibilidad con Service Fabric

Con las herramientas de Service Fabric en Visual Studio, puede desarrollar y depurar en Azure Service Fabric, ejecutar y depurar localmente e implementar en Azure.

::: moniker range="vs-2017"
La versión 15.9 y posterior de Visual Studio 2017 con la carga de trabajo de desarrollo de Azure instalada admite el desarrollo de microservicios en contenedores con contenedores de Windows y orquestación de Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 admite el desarrollo de microservicios en contenedores mediante contenedores de Windows y la orquestación de Service Fabric.
::: moniker-end

Para ver un tutorial detallado, consulte [Tutorial: Implementación de una aplicación .NET de un contenedor de Windows en Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Para más información sobre Azure Service Fabric, consulte [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Entrega continua e integración continua (CI/CD)

Visual Studio se integra fácilmente con Azure Pipelines para la integración continua y automatizada y la entrega de cambios en el código y la configuración del servicio. Para comenzar, consulte [Create your first pipeline](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2) (Creación de su primera canalización).

Para Service Fabric, consulte [Tutorial: Implementación de la aplicación de ASP.NET Core en Azure Service Fabric mediante Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Para Kubernetes, consulte [Deploy a Docker container app to Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops) (Implementación de una aplicación de contenedor de Docker en Azure Kubernetes Service).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre los servicios de implementación y el uso de herramientas de Visual Studio para trabajar con contenedores, lea los artículos siguientes:

[Depuración de aplicaciones en un contenedor de Docker local](edit-and-refresh.md)

[Implementación de un contenedor ASP.NET en un registro de contenedor con Visual Studio](hosting-web-apps-in-docker.md)
