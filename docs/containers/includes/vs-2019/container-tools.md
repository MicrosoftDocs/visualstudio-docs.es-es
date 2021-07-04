---
title: Visual Studio Tools para Docker con ASP.NET
author: ghogen
description: Aprenda a usar las herramientas de Visual Studio 2019 y Docker para Windows
ms.author: ghogen
ms.date: 02/22/2021
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 35beb1bb67dbfe4d0d1707c499b605f6ff698956
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2021
ms.locfileid: "112908164"
---
Con Visual Studio es muy fácil compilar, depurar y ejecutar aplicaciones .NET, ASP.NET y ASP.NET Core en contenedores y publicarlas en Azure Container Registry (ACR), Docker Hub, Azure App Service o un registro de contenedor propio. En este artículo se va a publicar una aplicación ASP.NET Core en ACR.

## <a name="prerequisites"></a>Requisitos previos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* [Herramientas de desarrollo de .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) para el desarrollo con .NET Core
* Para publicar en Azure Container Registry, una suscripción de Azure. [Regístrese para obtener una evaluación gratuita](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Instalación y configuración

Para instalar Docker, primero revise la información de [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker Desktop para Windows: información previa a la instalación). Después, instale [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Agregar un proyecto a un contenedor de Docker

1. Cree un proyecto con la plantilla **Aplicación web ASP.NET Core**, o bien, si quiere usar .NET Framework en lugar de .NET Core, elija **Aplicación web ASP.NET (.NET Framework)** .
1. En la pantalla **Información adicional**, asegúrese de que la casilla **Habilitar compatibilidad con Docker** está activada.

   ![Casilla Habilitar compatibilidad con Docker](../../media/container-tools/vs-2019/webapp-additional-information-31-docker.png)

   En la captura de pantalla se muestra .NET Core; si usa .NET Framework, tendrá un aspecto distinto.

1. Seleccione el tipo de contenedor que quiera (Windows o Linux) y haga clic en **Crear**.

## <a name="dockerfile-overview"></a>Información general sobre Dockerfile

Se agrega al proyecto un *Dockerfile*, la receta para crear una imagen de Docker final. Vea [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) (Referencia de Dockerfile) para obtener una descripción de los comandos que contiene.

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication1/WebApplication1.csproj", "WebApplication1/"]
RUN dotnet restore "WebApplication1/WebApplication1.csproj"
COPY . .
WORKDIR "/src/WebApplication1"
RUN dotnet build "WebApplication1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication1.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]
```

El elemento *Dockerfile* anterior se basa en la imagen [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e incluye instrucciones para modificar la imagen base mediante la creación del proyecto y la adición al contenedor. Si usa .NET Framework, la imagen base será distinta.

Si la casilla **Configurar para HTTPS** del cuadro de diálogo del nuevo proyecto está marcada, el *Dockerfile* expondrá dos puertos. Uno se utiliza para el tráfico HTTP, mientras que el otro se emplea para HTTPS. Si la casilla no está marcada, se expondrá un único puerto (80) para el tráfico HTTP.

## <a name="debug"></a>Depuración

Seleccione **Docker** en la lista desplegable de depuración de la barra de herramientas y empiece a depurar la aplicación. Es posible que vea un mensaje que pregunte sobre cómo confiar en un certificado; elija la opción de confiar en el certificado para continuar.

La opción **Herramientas de contenedor** de la ventana **Salida** muestra las acciones que están teniendo lugar. La primera vez, puede tardar unos minutos en descargar la imagen base, pero es mucho más rápido en ejecuciones posteriores.

>[!NOTE]
> Si necesita cambiar los puertos para la depuración, puede hacerlo en el archivo *launchSettings.json*. Vea [Configuración de inicio de contenedor](../../container-launch-settings.md).

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
1. En el cuadro de diálogo **Publicar**, seleccione la pestaña **Container Registry para Docker**.

   ![Captura de pantalla del cuadro de diálogo Publicar - Elegir Container Registry para Docker](../../media/container-tools/vs-2019/docker-container-registry.png)

1. Elija **Crear Azure Container Registry**.

   ![Captura de pantalla del cuadro de diálogo Publicar - Elegir Crear Azure Container Registry](../../media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

1. Rellene los valores deseados en el **Create a new Azure Container Registry** (Crear una nueva instancia de Azure Container Registry).

    | Parámetro      | Valor sugerido  | Descripción                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefijo de DNS** | Nombre único globalmente | Nombre que identifica de forma única el nuevo registro de contenedor. |
    | **Suscripción** | Elija una suscripción | La suscripción de Azure que se va a usar. |
    | **[Grupo de recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nombre del grupo de recursos en el que se va a crear el registro de contenedor. Elija **Nuevo** para crear un grupo de recursos nuevo.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Estándar | Nivel de servicio del registro de contenedor  |
    | **Ubicación del registro** | Una ubicación cercana a usted | Elija una ubicación en una [región](https://azure.microsoft.com/regions/) cercana a usted o a otros servicios que usarán el registro de contenedor. |

    ![Cuadro de diálogo Crear Azure Container Registry de Visual Studio][0]

1. Haga clic en **Crear**. En el cuadro de diálogo **Publicar** ahora se muestra el registro creado.

   ![Captura de pantalla del cuadro de diálogo Publicar que muestra Azure Container Registry creado](../../media/container-tools/vs-2019/created-azure-container-registry.png)

1. Elija **Finalizar** para completar el proceso de publicación de la imagen de contenedor en el registro recién creado en Azure.

   ![Captura de pantalla que muestra la publicación correcta](../../media/container-tools/vs-2019/publish-succeeded.png)

## <a name="next-steps"></a>Pasos siguientes

Ahora puede extraer el contenedor del registro a cualquier host capaz de ejecutar imágenes de Docker, por ejemplo [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
