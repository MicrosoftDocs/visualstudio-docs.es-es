---
title: Visual Studio Tools para Docker con ASP.NET Core
author: ghogen
description: Aprenda a usar las herramientas de Visual Studio 2019 y Docker para Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: d0da02773913a610c77d7165fdb0f9becfc59e9c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75927774"
---
Con Visual Studio es muy fácil compilar, depurar y ejecutar aplicaciones .NET, ASP.NET y ASP.NET Core en contenedores y publicarlas en Azure Container Registry (ACR), Docker Hub, Azure App Service o un registro de contenedor propio. En este artículo se va a publicar una aplicación ASP.NET Core en ACR.

## <a name="prerequisites"></a>Requisitos previos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* [Herramientas de desarrollo de .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) para el desarrollo con .NET Core 2.2
* Para publicar en Azure Container Registry, una suscripción de Azure. [Regístrese para obtener una evaluación gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalación y configuración

Para instalar Docker, primero revise la información de [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker Desktop para Windows: información previa a la instalación). Después, instale [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Agregar un proyecto a un contenedor de Docker

1. Cree un nuevo proyecto con la plantilla **Aplicación web ASP.NET Core**.
1. Seleccione **Aplicación web** y asegúrese de que la casilla **Habilitar compatibilidad con Docker** esté activada.

   ![Casilla Habilitar compatibilidad con Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Seleccione el tipo de contenedor que quiera (Windows o Linux) y haga clic en **Crear**.

## <a name="dockerfile-overview"></a>Información general sobre Dockerfile

Se agrega al proyecto un *Dockerfile*, la receta para crear una imagen de Docker final. Vea [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) (Referencia de Dockerfile) para obtener una descripción de los comandos que contiene.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

El elemento *Dockerfile* anterior se basa en la imagen [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e incluye instrucciones para modificar la imagen base mediante la creación del proyecto y la adición al contenedor.

Si la casilla **Configurar para HTTPS** del cuadro de diálogo del nuevo proyecto está marcada, el *Dockerfile* expondrá dos puertos. Uno se utiliza para el tráfico HTTP, mientras que el otro se emplea para HTTPS. Si la casilla no está marcada, se expondrá un único puerto (80) para el tráfico HTTP.

## <a name="debug"></a>Depuración

Seleccione **Docker** en la lista desplegable de depuración de la barra de herramientas y empiece a depurar la aplicación. Es posible que vea un mensaje que pregunte sobre cómo confiar en un certificado; elija la opción de confiar en el certificado para continuar.

La opción **Herramientas de contenedor** de la ventana **Salida** muestra las acciones que están teniendo lugar.

## <a name="containers-window"></a>Ventana Contenedores

Si tiene la versión 16.4 u otra posterior de Visual Studio 2019, puede usar la ventana **Contenedores** para consultar los contenedores en ejecución en la máquina, así como las imágenes disponibles.

Abra la ventana **Contenedores** mediante el cuadro de búsqueda del IDE (**Ctrl**+**Q**), escriba `container` y elija la ventana **Contenedores** de la lista.

Puede colocar la ventana **Contenedores** en un lugar fácilmente accesible, como debajo del editor; para ello, muévala siguiendo las guías de colocación de ventanas.

En la ventana, busque el contenedor y recorra cada pestaña para ver las variables de entorno, las asignaciones de puertos, los registros y el sistema de archivos.

![Captura de pantalla de la ventana Contenedores](../../media/overview/vs-2019/container-tools-window.png)

Para obtener más información, vea [Visualización y diagnóstico de contenedores e imágenes en Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publicar imágenes de Docker

Una vez completado el ciclo de desarrollo y depuración de la aplicación, puede crear una imagen de producción de la aplicación.

1. Cambie la lista desplegable de configuración a **Versión** y compile la aplicación.
1. Haga clic con el botón derecho en el **Explorador de soluciones** y elija **Publicar**.
1. En el cuadro de diálogo de destino de publicación, seleccione la pestaña **Container Registry**.
1. Elija **Crear una instancia de Azure Container Registry** y haga clic en **Publicar**.
1. Rellene los valores deseados en el **Create a new Azure Container Registry** (Crear una nueva instancia de Azure Container Registry).

    | Parámetro      | Valor sugerido  | Descripción                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefijo de DNS** | Nombre único globalmente | Nombre que identifica de forma única el nuevo registro de contenedor. |
    | **Suscripción** | Elija una suscripción | La suscripción de Azure que se va a usar. |
    | **[Grupo de recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nombre del grupo de recursos en el que se va a crear el registro de contenedor. Elija **Nuevo** para crear un grupo de recursos nuevo.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Estándar | Nivel de servicio del registro de contenedor  |
    | **Ubicación del registro** | Una ubicación cercana a usted | Elija una ubicación en una [región](https://azure.microsoft.com/regions/) cercana a usted o a otros servicios que usarán el registro de contenedor. |

    ![Cuadro de diálogo Crear Azure Container Registry de Visual Studio][0]

1. Haga clic en **Crear**

   ![Captura de pantalla que muestra la publicación correcta](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Pasos siguientes

Ahora puede extraer el contenedor del registro a cualquier host capaz de ejecutar imágenes de Docker, por ejemplo [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
