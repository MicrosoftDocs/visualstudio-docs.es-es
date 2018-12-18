---
title: Tutorial de las herramientas de Kubernetes | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 8cf4192ce0f925624dbbe890381d3557f2a27223
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942938"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Introducción a Visual Studio Tools de Kubernetes

Las herramientas de Kubernetes de Visual Studio ayudan a simplificar el desarrollo de aplicaciones en contenedores como destino de Kubernetes. Visual Studio puede crear automáticamente los archivos de configuración como código necesarios para admitir la implementación de Kubernetes, como gráficos Dockerfiles y Helm. Puede depurar el código en un clúster activo de Azure Kubernetes Service (AKS) con espacios de desarrollo de Azure, o publicar directamente en un clúster de AKS desde dentro de Visual Studio.

Este tutorial trata con Visual Studio para agregar compatibilidad con Kubernetes a un proyecto y publicar en AKS. Si interesa principalmente utilizar [espacios de desarrollo de Azure](http://aka.ms/get-azds) para depurar y probar el proyecto en AKS, puede ir a la [tutorial de Azure Dev espacios](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio) en su lugar.

## <a name="prerequisites"></a>Requisitos previos

Para aprovechar esta nueva funcionalidad, necesitará:

- La versión más reciente de [Visual Studio 2017](https://visualstudio.microsoft.com/download) con el *ASP.NET y desarrollo web* carga de trabajo.

- El [Kubernetes tools para Visual Studio](https://aka.ms/get-vsk8stools), disponible como una descarga independiente.

- [Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows) instalado en su estación de trabajo de desarrollo (es decir, donde se ejecuta Visual Studio), si desea compilar imágenes de Docker, depurar contenedores de Docker que se ejecutan localmente, o publicar en AKS. (Docker es *no* necesarios para compilar y depurar los contenedores de Docker en AKS con espacios de desarrollo de Azure.)

- Si desea publicar en AKS desde Visual Studio (*no* necesarios para la depuración en AKS con espacios de desarrollo de Azure):

    1.  El [AKS herramientas de publicación](https://aka.ms/get-vsk8spublish), disponible como una descarga independiente.

    1.  Un clúster de Azure Kubernetes Service. Para obtener más información, consulte [crear un clúster de AKS](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster). No olvide [conectarse al clúster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) desde su estación de trabajo de desarrollo.

    1.  Helm CLI instalada en su estación de trabajo de desarrollo. Para obtener más información, consulte [instalar Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1.  Configurado en el clúster AKS mediante el uso de helm la `helm init` comando. Para obtener más información sobre cómo hacerlo, consulte [cómo configurar Helm](/azure/aks/kubernetes-helm#configure-helm).

## <a name="create-a-new-kubernetes-project"></a>Cree un nuevo proyecto de Kubernetes

Una vez que tenga instaladas las herramientas adecuadas, inicie Visual Studio y cree un nuevo proyecto. En **en la nube**, elija el **aplicación contenedora para Kubernetes** tipo de proyecto. Seleccione este tipo de proyecto y elija **Aceptar**.

![Captura de pantalla de crear un nuevo proyecto de aplicación de Kubernetes](media/k8s-tools-new-k8s-app.png)

A continuación, puede elegir a qué tipo de ASP.NET Core en la aplicación web para crear. Elija **aplicación Web** y elija **Aceptar**. El habitual **habilitar la compatibilidad con Docker** opción no aparece en este cuadro de diálogo.  Compatibilidad con docker está habilitada de forma predeterminada para una aplicación contenedora para Kubernetes.

![Captura de pantalla de selección de la aplicación web](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Agregar compatibilidad con Kubernetes a un proyecto existente

Como alternativa, puede agregar compatibilidad con Kubernetes para un proyecto de aplicación web de ASP.NET Core existente. Para ello, haga doble clic en el proyecto y elija **agregar** > **la compatibilidad con el orquestador de contenedor**.

![Elemento de menú de la captura de pantalla de orquestador de contenedores agregar](media/k8s-tools-add-container-orchestrator.png)

En el cuadro de diálogo, seleccione "Kubernetes y Helm" y elija **Aceptar**.

![Cuadro de diálogo de captura de pantalla de orquestador de contenedores agregar](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Lo que Visual Studio crea automáticamente

Después de crear un nuevo **aplicación contenedora para Kubernetes** proyecto o agregando compatibilidad con orquestador de contenedores de Kubernetes a un proyecto existente, verá que algunos archivos adicionales en el proyecto que facilitan la implementación en Kubernetes.

![Captura de pantalla del explorador de soluciones después de agregar compatibilidad con el orquestador de contenedor](media/k8s-tools-solution-explorer.png)

Los archivos agregados son:

- un archivo Dockerfile, que le permite generar un Docker imagen de contenedor que hospeda esta aplicación web. Como verá, las herramientas de Visual Studio aprovecha este Dockerfile al depurar e implementar en Kubernetes. Si prefiere trabajar directamente con la imagen de Docker, puede hacer doble clic en el archivo Dockerfile y elegir **compilar imagen de Docker**.

   ![Opción de captura de pantalla de la imagen de Docker de compilación](media/k8s-tools-build-docker-image.png)

- un gráfico de Helm y un *gráficos* carpeta. Estos archivos yaml constituyen el gráfico de Helm para la aplicación, que puede usar para implementarla en Kubernetes. Para obtener más información sobre Helm, consulte [ https://www.helm.sh ](https://www.helm.sh).

- *azds.yaml*. Esto contiene la configuración para los espacios de desarrollo de Azure, que proporciona una experiencia de depuración iterativa rápida en Azure Kubernetes Service. Para obtener más información, consulte [la documentación de Azure Dev espacios](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publicar en Azure Kubernetes Service (AKS)

Con todos estos archivos en su lugar, puede usar el IDE de Visual Studio para escribir y depurar el código de aplicación, igual que siempre tiene. También puede usar [Azure Dev espacios](http://aka.ms/get-azds) rápidamente, ejecutar y depurar el código que se ejecuta en directo en un clúster de AKS. Para obtener más información, consulte el [tutorial de espacios de desarrollo de Azure](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio)

Una vez que tenga el código que se ejecuta como quiera, puede publicar directamente desde Visual Studio en un clúster de AKS.

Para ello, primero debe comprobar que se ha instalado todo el contenido como se describe en el [requisitos previos](#prerequisites) sección bajo el elemento para la publicación en AKS y ejecutar todos los pasos de la línea de comandos en los vínculos. A continuación, configure un perfil de publicación que publica la imagen de contenedor en Azure Container Registry (ACR). A continuación, puede extraer la imagen de contenedor de ACR y su implementación en el clúster de AKS.

1. En **el Explorador de soluciones**, haga doble clic en su *proyecto* y elija **publicar**.

   ![Captura de pantalla de publicar el elemento de menú](media/k8s-tools-publish-project.png)

2. En el **publicar** , elija **Container Registry** como la publicación de destino y siga las indicaciones para seleccionar el registro de contenedor. Si no dispone de un registro de contenedor, elija **crear instancia de Azure Container Registry** crear uno desde Visual Studio. Para obtener más información, consulte [publicar el contenedor en Azure Container Registry](#publish-your-container-to-azure-container-registry).

   ![Captura de pantalla de selección una pantalla de destino de publicación](media/k8s-tools-publish-to-acr.png)

3. En el Explorador de soluciones, haga clic en su *solución* y haga clic en **publicar en Azure AKS**.

   ![Captura de pantalla de la publicación para el elemento de menú de Azure AKS](media/k8s-tools-publish-solution.png)

4. Elija la suscripción y el clúster de AKS, junto con el ACR publicar el perfil que acaba de crear. A continuación, haga clic en **Aceptar**.

   ![Captura de pantalla de publicar en la pantalla AKS](media/k8s-tools-publish-to-aks.png)

   Esto le llevará a la **publicar en Azure AKS** pantalla.

5. Elija la **Helm configurar** vínculo para actualizar la línea de comandos usada para instalar los gráficos de Helm en el servidor.

   ![Vínculo de captura de pantalla de configuración de Helm](media/k8s-tools-configure-helm.png)

   Actualización de la línea de comandos es útil si hay argumentos de línea de comandos personalizada que desea especificar como un nombre diferente de contexto o un gráfico de Kubernetes.

   ![Captura de pantalla de Helm configurar pantalla](media/k8s-tools-helm-configure-screen.png)

6. Cuando esté listo para implementar, haga clic en el **publicar** botón para publicar la aplicación en AKS.

   ![Captura de pantalla de publicar en pantalla de Azure AKS](media/k8s-tools-publish-screen.png)

¡Enhorabuena! Ahora puede usar toda la eficacia de Visual Studio para el desarrollo de aplicaciones de Kubernetes.

## <a name="next-steps"></a>Pasos siguientes

Más información sobre el desarrollo de Kubernetes en Azure, lea el [documentación de AKS](/azure/aks).

Más información sobre los espacios de desarrollo de Azure, lea el [documentación de espacios de desarrollo de Azure](http://aka.ms/get-azds)
