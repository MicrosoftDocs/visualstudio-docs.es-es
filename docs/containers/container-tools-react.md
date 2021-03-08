---
title: Herramientas de contenedor de Visual Studio con ASP.NET Core y React.js
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: Aprenda a crear una aplicación de React SPA en contenedor con herramientas de contenedor de Visual Studio y Docker
ms.author: ghogen
ms.date: 02/21/2021
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 7a2a9e7c8b2c53dcee7f11d4b0b795b66ab80a80
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684351"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Inicio rápido: Uso de Docker con una aplicación de página única de React en Visual Studio

Con Visual Studio, es muy fácil compilar, depurar y ejecutar aplicaciones ASP.NET Core en contenedores, incluidas aquellas con JavaScript en el lado cliente (como una aplicación de página única de React.js), y publicarlas en Azure Container Registry (ACR), Docker Hub, Azure App Service o en su propio registro de contenedor. En este artículo, realizaremos la publicación en ACR.

## <a name="prerequisites"></a>Requisitos previos

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* Para publicar en Azure Container Registry, una suscripción de Azure. [Regístrese para obtener una evaluación gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Para los contenedores de Windows, Windows 10 versión 1903 o posterior, para usar las imágenes de Docker a las que se hace referencia en este artículo.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* [Herramientas de desarrollo de .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) para el desarrollo con .NET Core 3.1.
* Para publicar en Azure Container Registry, una suscripción de Azure. [Regístrese para obtener una evaluación gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
* [Node.js](https://nodejs.org/en/download/)
* Para los contenedores de Windows, Windows 10 versión 1903 o posterior, para usar las imágenes de Docker a las que se hace referencia en este artículo.
::: moniker-end

## <a name="installation-and-setup"></a>Instalación y configuración

Para instalar Docker, primero revise la información de [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker Desktop para Windows: información previa a la instalación). Después, instale [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Creación de un proyecto y adición de compatibilidad con Docker

::: moniker range="vs-2017"
1. Cree un nuevo proyecto con la plantilla **Aplicación web ASP.NET Core**.
1. Seleccione **React.js**. No puede seleccionar **Habilitar compatibilidad con Docker**, pero no se preocupe, puede agregar esa compatibilidad después de crear el proyecto.

   ![Captura de pantalla del nuevo proyecto React.js](media/container-tools-react/vs-2017/new-react-project.png)

1. Haga clic con el botón derecho en el nodo del proyecto y elija **Agregar**>**Compatibilidad con Docker** para agregar un archivo Dockerfile al proyecto.

   ![Adición de compatibilidad con Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Seleccione el tipo de contenedor y haga clic en **Aceptar**.
::: moniker-end

::: moniker range=">=vs-2019"

1. Cree un nuevo proyecto con la plantilla **ASP.NET Core con React.js**.

   ![Captura de pantalla de la creación de un nuevo proyecto de React.js](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. En la pantalla **Información adicional**, no puede seleccionar **Habilitar compatibilidad con Docker**, pero no se preocupe, puede agregar esa compatibilidad más adelante.

   ![Captura de pantalla de la creación de un nuevo proyecto de React.js: pantalla Información adicional](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. Haga clic con el botón derecho en el nodo del proyecto y elija **Agregar**>**Compatibilidad con Docker** para agregar un archivo Dockerfile al proyecto.

   ![Adición de compatibilidad con Docker](media/container-tools-react/vs-2017/add-docker-support.png)

1. Seleccione el tipo de contenedor.
::: moniker-end

El siguiente paso es diferente en función de si usa contenedores de Linux o contenedores de Windows.

## <a name="modify-the-dockerfile-linux-containers"></a>Modificación de Dockerfile (contenedores de Linux)

Se agrega al proyecto un *Dockerfile*, la receta para crear una imagen de Docker final. Vea [Dockerfile reference (Referencia de Dockerfile)](https://docs.docker.com/engine/reference/builder/) para obtener una descripción de los comandos que contiene.

Abra el archivo *Dockerfile* en el proyecto y agregue las líneas siguientes para instalar Node.js 10.x en el contenedor. Asegúrese de agregar estas dos líneas en la primera sección, para agregar la instalación del administrador de paquetes de Node *npm.exe* a la imagen base, así como a la sección `build`.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

El archivo *Dockerfile* debería tener ahora un aspecto similar al siguiente:

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication-ReactSPA/WebApplication-ReactSPA.csproj", "WebApplication-ReactSPA/"]
RUN dotnet restore "WebApplication-ReactSPA/WebApplication-ReactSPA.csproj"
COPY . .
WORKDIR "/src/WebApplication-ReactSPA"
RUN dotnet build "WebApplication-ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-ReactSPA.dll"]
```

El elemento *Dockerfile* anterior se basa en la imagen [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) e incluye instrucciones para modificar la imagen base mediante la creación del proyecto y su incorporación al contenedor.

Si la casilla **Configurar para HTTPS** del cuadro de diálogo del nuevo proyecto está marcada, el *Dockerfile* expondrá dos puertos. Uno se utiliza para el tráfico HTTP, mientras que el otro se emplea para HTTPS. Si la casilla no está marcada, se expondrá un único puerto (80) para el tráfico HTTP.

## <a name="modify-the-dockerfile-windows-containers"></a>Modificación de Dockerfile (contenedores de Windows)

Abra el archivo de proyecto; para ello, haga doble clic en el nodo del proyecto y actualice el archivo de proyecto (*.csproj) agregando la siguiente propiedad como elemento secundario del elemento `<PropertyGroup>`:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Actualice Dockerfile agregando las líneas siguientes. Esta acción copiará node y npm en el contenedor.

   1. Agregue ``# escape=` `` a la primera línea de Dockerfile
   1. Agregue las líneas siguientes delante de `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Agregue la línea siguiente delante y después de `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. El archivo Dockerfile completo debería tener ahora un aspecto similar al siguiente:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplicationReact1/WebApplicationReact1.csproj", "WebApplicationReact1/"]
      RUN dotnet restore "WebApplicationReact1/WebApplicationReact1.csproj"
      COPY . .
      WORKDIR "/src/WebApplicationReact1"
      RUN dotnet build "WebApplicationReact1.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplicationReact1.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplicationReact1.dll"]
      ```

   1. Actualice el archivo .dockerignore quitando `**/bin`.

## <a name="debug"></a>Depuración

Seleccione **Docker** en la lista desplegable de depuración de la barra de herramientas y empiece a depurar la aplicación. Es posible que vea un mensaje que pregunte sobre cómo confiar en un certificado; elija la opción de confiar en el certificado para continuar.  La primera vez que compila, Docker descarga las imágenes base, por lo que puede tardar un poco más.

La opción **Herramientas de contenedor** de la ventana **Salida** muestra las acciones que están teniendo lugar. Debería ver los pasos de instalación asociados con *npm.exe*.

El explorador muestra la página principal de la aplicación.

::: moniker range="vs-2017"
   ![Captura de pantalla de la aplicación en ejecución](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Captura de pantalla de la aplicación en ejecución](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

Intente navegar a la página *Contador* y pruebe el código del lado cliente para el contador haciendo clic en el botón **Incremento**.

Abra la **Consola del Administrador de paquetes** (PMC) desde el menú **Herramientas** > Administrador de paquetes NuGet, **Consola del Administrador de paquetes**.

Seguidamente, se aplica la etiqueta *dev* a la imagen de Docker resultante de la aplicación. La imagen se basa en la etiqueta *3.1-nanoserver-1903* de la imagen base *dotnet/core/aspnet*. Ejecute el comando `docker images` en la ventana **Consola del Administrador de paquetes** (PMC). Se muestran las imágenes en la máquina:

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1-buster-slim     e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> La imagen **dev** no contiene los archivos binarios de la aplicación ni otro contenido, ya que las configuraciones de **Depurar** usan el montaje de volumen para proporcionar la experiencia de depuración y edición iterativa. Para crear una imagen de producción que contenga todo el contenido, use la configuración de **Liberar**.

Ejecute el comando `docker ps` en la PMC. Tenga en cuenta que la aplicación se ejecuta mediante el contenedor:

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-React1
```

## <a name="publish-docker-images"></a>Publicar imágenes de Docker

Una vez completado el ciclo de desarrollo y depuración de la aplicación, puede crear una imagen de producción de la aplicación.

:::moniker range="vs-2017"

1. Cambie la lista desplegable de configuración a **Versión** y compile la aplicación.
1. Haga clic con el botón derecho en el **Explorador de soluciones** y elija **Publicar**.
1. En el cuadro de diálogo de destino de publicación, seleccione **Container Registry**.
1. Elija **Crear una instancia de Azure Container Registry** y haga clic en **Publicar**.
1. Rellene los valores deseados en el **Create a new Azure Container Registry** (Crear una nueva instancia de Azure Container Registry).

    | Parámetro      | Valor sugerido  | Descripción                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefijo de DNS** | Nombre único globalmente | Nombre que identifica de forma única el nuevo registro de contenedor. |
    | **Suscripción** | Elija una suscripción | La suscripción de Azure que se va a usar. |
    | **[Grupo de recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nombre del grupo de recursos en el que se va a crear el registro de contenedor. Elija **Nuevo** para crear un grupo de recursos nuevo.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Estándar | Nivel de servicio del registro de contenedor  |
    | **Ubicación del registro** | Una ubicación cercana a usted | Elija una ubicación en una [región](https://azure.microsoft.com/regions/) cercana a usted o a otros servicios que usarán el registro de contenedor. |

    ![Cuadro de diálogo Crear Azure Container Registry de Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. Seleccione **Crear**.

   ![Captura de pantalla que muestra la publicación correcta](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. Cambie la lista desplegable de configuración a **Versión** y compile la aplicación.
1. Haga clic con el botón derecho en el **Explorador de soluciones** y elija **Publicar**.
1. En el cuadro de diálogo de destino de publicación, seleccione **Container Registry para Docker**.

   ![Elija Container Registry para Docker.](media/container-tools-react/vs-2019/publish-dialog1.png)

1. Después, elija **Azure Container Registry**.

   ![Elija Azure Container Registry.](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. Elija **Crear una instancia de Azure Container Registry**.
1. Rellene los valores deseados en la pantalla **Crear una instancia de Azure Container Registry**.

    | Parámetro      | Valor sugerido  | Descripción                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefijo de DNS** | Nombre único globalmente | Nombre que identifica de forma única el nuevo registro de contenedor. |
    | **Suscripción** | Elija una suscripción | La suscripción de Azure que se va a usar. |
    | **[Grupo de recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nombre del grupo de recursos en el que se va a crear el registro de contenedor. Elija **Nuevo** para crear un grupo de recursos nuevo.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Estándar | Nivel de servicio del registro de contenedor  |
    | **Ubicación del registro** | Una ubicación cercana a usted | Elija una ubicación en una [región](https://azure.microsoft.com/regions/) cercana a usted o a otros servicios que usarán el registro de contenedor. |

    ![Cuadro de diálogo Crear Azure Container Registry de Visual Studio](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. Seleccione **Crear** y, después, **Finalizar**.

   ![Seleccionar o crear una nueva instancia de ACR](media/container-tools-react/vs-2019/publish-dialog2.png)

   Una vez finalizado el proceso de publicación, puede revisar la configuración de publicación y editarla, si es necesario, o bien volver a publicar la imagen con el botón **Publicar**.

   ![Captura de pantalla que muestra la publicación correcta](media/container-tools-react/vs-2019/publish-finished.png)

   Para volver a empezar mediante el cuadro de diálogo **Publicar**, elimine el perfil de publicación mediante el vínculo **Eliminar** de esta página y, después, vuelva a seleccionar **Publicar**.
:::moniker-end

## <a name="next-steps"></a>Pasos siguientes

Ahora puede extraer el contenedor del registro a cualquier host capaz de ejecutar imágenes de Docker, por ejemplo [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Recursos adicionales

* [Desarrollo de contenedores con Visual Studio](./index.yml)
* [Troubleshoot Visual Studio development with Docker](troubleshooting-docker-errors.md) (Solución de problemas de desarrollo de Visual Studio con Docker)
* [Visual Studio Container Tools GitHub repository](https://github.com/Microsoft/DockerTools) (Repositorio de GitHub de herramientas de contenedor de Visual Studio)

