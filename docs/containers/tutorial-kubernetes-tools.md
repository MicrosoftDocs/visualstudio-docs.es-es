---
title: Tutorial sobre las herramientas de Kubernetes | Microsoft Docs
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 45397ddf21f1ea1d735c2753864e5954850a4d98
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126116"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Introducción a Visual Studio Tools para Kubernetes

Visual Studio Tools para Kubernetes ayuda a simplificar el desarrollo de aplicaciones en contenedor destinadas a Kubernetes. Visual Studio puede crear automáticamente los archivos de configuración como código necesarios para admitir la implementación de Kubernetes, como Dockerfiles y gráficos de Helm. Puede depurar el código en un clúster activo de Azure Kubernetes Service (AKS) mediante Azure Dev Spaces o bien publicar directamente en un clúster de AKS desde Visual Studio.

En este tutorial se trata el uso de Visual Studio para agregar compatibilidad con Kubernetes a un proyecto y publicar en AKS. Si su principal interés es usar [Azure Dev Spaces](https://aka.ms/get-azds) para depurar y probar el proyecto que se ejecuta en AKS, puede ir directamente al [tutorial de Azure Dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio).

## <a name="prerequisites"></a>Requisitos previos

Para aprovechar esta nueva funcionalidad, necesita:

::: moniker range="vs-2017"
- La versión más reciente de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con la carga de trabajo *ASP.NET y desarrollo web*.
- [Visual Studio Tools para Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponible como descarga independiente.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con la carga de trabajo de *ASP.NET y desarrollo web*.
::: moniker-end
- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) instalado en la estación de trabajo de desarrollo (es decir, donde se ejecuta Visual Studio) si quiere compilar imágenes de Docker, depurar contenedores de Docker que se ejecutan localmente o publicar en AKS. (Docker *no* es necesario para compilar y depurar contenedores de Docker en AKS mediante Azure Dev Spaces).
::: moniker range="vs-2017"
- Si quiere publicar en AKS desde Visual Studio (*no* necesario para la depuración en AKS mediante Azure Dev Spaces):

    1. Las [herramientas de publicación de AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibles como descarga independiente.

    1. Un clúster de Azure Kubernetes Service. Para obtener más información, vea [Creación de un clúster de AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Asegúrese de [conectarse al clúster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) desde la estación de trabajo de desarrollo.

    1. CLI de Helm instalada en la estación de trabajo de desarrollo. Para obtener más información, vea [Instalación de Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1. Helm configurado en el clúster de AKS mediante el comando `helm init`. Para obtener más información sobre cómo hacerlo, vea [Cómo configurar Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Creación de un nuevo proyecto de Kubernetes

::: moniker range="vs-2017"

Una vez que tenga instaladas las herramientas adecuadas, inicie Visual Studio y cree un nuevo proyecto. En **Nube**, seleccione el tipo de proyecto **Aplicación contenedora para Kubernetes**. Seleccione este tipo de proyecto y luego **Aceptar**.

![Captura de pantalla de la creación de un nuevo proyecto de aplicación de Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

En la ventana de inicio de Visual Studio, busque *Kubernetes* y seleccione **Aplicación contenedora para Kubernetes**.

![Captura de pantalla de la creación de un nuevo proyecto de aplicación de Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Proporcione el nombre del proyecto.

![Captura de pantalla de la creación de un nuevo proyecto de aplicación de Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Luego puede elegir el tipo de aplicación web de ASP.NET Core que se va a crear. Seleccione **Aplicación web**. La opción habitual **Habilitar compatibilidad con Docker** no aparece en este cuadro de diálogo.  La compatibilidad con Docker está habilitada de forma predeterminada para una aplicación contenedora de Kubernetes.

::: moniker range="vs-2017"

![Captura de pantalla de la selección de aplicación web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Captura de pantalla de la selección de aplicación web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Incorporación de compatibilidad con Kubernetes a un proyecto existente

También puede agregar compatibilidad con Kubernetes a un proyecto de aplicación web de ASP.NET Core existente. Para ello, haga clic con el botón derecho en el proyecto y seleccione **Agregar** > **Compatibilidad con el orquestador de contenedores**.

::: moniker range="vs-2017"

![Captura de pantalla del elemento de menú Agregar compatibilidad con el orquestador de contenedores](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Captura de pantalla del elemento de menú Agregar compatibilidad con el orquestador de contenedores](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

En el cuadro de diálogo, seleccione **Kubernetes/Helm** y luego **Aceptar**.

![Captura de pantalla del cuadro de diálogo Agregar compatibilidad con el orquestador de contenedores](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Lo que Visual Studio crea automáticamente

Después de crear un nuevo proyecto **Aplicación contenedora para Kubernetes** o de agregar compatibilidad con el orquestador de contenedores de Kubernetes a un proyecto existente, aparecen algunos archivos adicionales en el proyecto que facilitan la implementación en Kubernetes.

::: moniker range="vs-2017"

![Captura de pantalla del Explorador de soluciones después de agregar compatibilidad con el orquestador de contenedores](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Captura de pantalla del Explorador de soluciones después de agregar compatibilidad con el orquestador de contenedores](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Los archivos agregados son:

- un Dockerfile, que permite generar una imagen de contenedor de Docker que hospeda esta aplicación web. Como se ve, Visual Studio Tools aprovecha este Dockerfile al depurar e implementar en Kubernetes. Si prefiere trabajar directamente con la imagen de Docker, puede hacer clic con el botón derecho en el Dockerfile y seleccionar **Compilar imagen de Docker**.

   ![Captura de pantalla de la opción Compilar imagen de Docker](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- un gráfico de Helm y una carpeta *charts*. Estos archivos yaml componen el gráfico de Helm de la aplicación, que puede usar para implementar en Kubernetes. Para obtener más información sobre Helm, vea [https://www.helm.sh](https://www.helm.sh).

- *azds.yaml*. Contiene la configuración de Azure Dev Spaces, que proporciona una experiencia de depuración rápida e iterativa en Azure Kubernetes Service. Para obtener más información, vea la [documentación de Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publicación en Azure Kubernetes Service (AKS)

Con todos estos archivos en su lugar, puede usar el IDE de Visual Studio para escribir y depurar el código de aplicación como siempre lo ha hecho. También puede usar [Azure Dev Spaces](https://aka.ms/get-azds) para ejecutar y depurar rápidamente el código que se ejecuta en vivo en un clúster de AKS. Para obtener más información, vea el [tutorial de Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio)

Una vez que el código se esté ejecutando de la manera deseada, puede publicar directamente desde Visual Studio en un clúster de AKS.

Para ello, primero debe comprobar que ha instalado todo lo indicado en la sección [Requisitos previos](#prerequisites) bajo el elemento para publicar en AKS y ejecutar todos los pasos de la línea de comandos proporcionados en los vínculos. Luego configure un perfil de publicación que publique la imagen de contenedor en Azure Container Registry (ACR). Después, AKS puede extraer la imagen de contenedor de ACR e implementarla en el clúster.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el *proyecto* y seleccione **Publicar**.

   ![Captura de pantalla del elemento de menú Publicar](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. En la pantalla **Publicar**, seleccione **Registro de contenedor** como destino de publicación y siga las indicaciones para seleccionar el registro de contenedor. Si aún no tiene un registro de contenedor, seleccione **Crear una instancia de Azure Container Registry** para crear uno desde Visual Studio. Para obtener más información, vea [Publicación del contenedor en Azure Container Registry](vs-azure-tools-docker-hosting-web-apps-in-docker.md).

   ![Captura de la pantalla para seleccionar un destino de publicación](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. De nuevo en el Explorador de soluciones, haga clic con el botón derecho en la *solución* y haga clic en **Publicar en Azure AKS**.

   ![Captura de pantalla del elemento de menú Publicar en Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Seleccione la suscripción y el clúster de AKS, junto con el perfil de publicación de ACR que acaba de crear. A continuación, haga clic en **Aceptar**.

   ![Captura de la pantalla Publicar en AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Esto lleva a la pantalla **Publicar en Azure AKS**.

5. Seleccione el vínculo **Configurar Helm** para actualizar la línea de comandos que se usa para instalar los gráficos de Helm en el servidor.

   ![Captura de pantalla de Configurar Helm](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   La actualización de la línea de comandos es útil si hay argumentos de línea de comandos personalizados que quiera especificar, como otro contexto de Kubernetes o nombre de gráfico.

   ![Captura de la pantalla de configuración de Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Cuando esté listo para realizar la implementación, haga clic en el botón **Publicar** para publicar la aplicación en AKS.

   ![Captura de pantalla de la publicación en Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

¡Enhorabuena! Ahora puede usar todo el potencial de Visual Studio para el desarrollo de aplicaciones de Kubernetes.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre el desarrollo de Kubernetes en Azure, lea la [documentación de AKS](/azure/aks).

Para obtener más información sobre Azure Dev Spaces, lea la [documentación de Azure Dev Spaces](https://aka.ms/get-azds)
