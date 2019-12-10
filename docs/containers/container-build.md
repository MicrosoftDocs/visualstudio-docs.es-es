---
title: Introducción a la compilación y la depuración en las herramientas de contenedor de Visual Studio
author: ghogen
description: Introducción al proceso de compilación y depuración en las herramientas de contenedor
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: e1b2f332563503dcb4d63faf301000db83eed5ea
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74706795"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Compilación de aplicaciones en contenedores con Visual Studio

Tanto si va a compilar desde el IDE de Visual Studio como si va a configurar una compilación de línea de comandos, debe conocer la forma en que Visual Studio usa el archivo Dockerfile para compilar los proyectos.  Por motivos de rendimiento, Visual Studio sigue un proceso especial para las aplicaciones en contenedores. Entender cómo Visual Studio compila los proyectos es particularmente importante al personalizar el proceso de compilación modificando el archivo Dockerfile.

Cuando Visual Studio compila un proyecto que no usa contenedores de Docker, invoca a MSBuild en el equipo local y genera los archivos de salida en una carpeta (normalmente `bin`) dentro de la carpeta de local de la solución. Sin embargo, en un proyecto en contenedores el proceso de compilación tiene en cuenta las instrucciones del archivo Dockerfile para compilar la aplicación en contenedores. El archivo Dockerfile que usa Visual Studio se divide en varias fases. Este proceso se basa en la característica de *compilación de varias fases* de Docker.

## <a name="multistage-build"></a>Compilación de varias fases

La característica de compilación de varias fases hace más eficaz el proceso de compilación de contenedores y hace que los contenedores sean más pequeños, lo que les permite contener solo los bits que la aplicación necesita en tiempo de ejecución. La compilación de varias fases se usa para los proyectos de .NET Core, no para los proyectos de .NET Framework.

La compilación de varias fases permite crear imágenes de contenedor en fases que producen imágenes intermedias. Por ejemplo, considere un archivo Dockerfile típico generado por Visual Studio. La primera fase es `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Las líneas del Dockerfile comienzan con la imagen de Nano Server de Microsoft Container Registry (mcr.microsoft.com) y crean una imagen intermedia `base` que expone los puertos 80 y 443 y establece el directorio de trabajo en `/app`.

La siguiente fase es `build`, que se muestra de la siguiente manera:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Puede ver que la fase `build` se inicia a partir de una imagen original diferente del registro (`sdk`, en vez de `aspnet`), en lugar de continuar desde la base.  La imagen `sdk` tiene todas las herramientas de compilación y, por esa razón, es mucho más grande que la imagen ASPNET, que solo contiene componentes en tiempo de ejecución. El motivo por el que se usa una imagen independiente queda claro cuando se examina el resto del archivo Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La fase final se inicia de nuevo desde `base` e incluye `COPY --from=publish` para copiar la salida publicada en la imagen final. Este proceso permite que la imagen final sea mucho más pequeña, ya que no tiene que incluir todas las herramientas de compilación que se encontraban en la imagen `sdk`.

## <a name="building-from-the-command-line"></a>Compilar desde la línea de comandos

Si quiere compilar fuera de Visual Studio, puede usar `docker build` o `MSBuild` para hacerlo desde la línea de comandos.

### <a name="docker-build"></a>docker build

Para compilar una solución en contenedores desde la línea de comandos, normalmente puede usar el comando `docker build <context>` para cada proyecto de la solución. Proporcione el argumento *build context*. El *contexto de compilación* para un archivo Dockerfile es la carpeta del equipo local que se usa como carpeta de trabajo para generar la imagen. Por ejemplo, es la carpeta desde la que se copian los archivos cuando copia en el contenedor.  En los proyectos de .NET Core, use la carpeta que contiene el archivo de solución (.sln).  Expresado como una ruta de acceso relativa, este argumento suele ser ".." para un archivo Dockerfile en una carpeta del proyecto y el archivo de solución en su carpeta principal.  En el caso de los proyectos de .NET Framework, el contexto de compilación es la carpeta del proyecto, no la carpeta de la solución.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Los archivos Dockerfile creados por Visual Studio para proyectos de .NET Framework (y para proyectos de .NET Core creados con versiones de Visual Studio anteriores a Visual Studio 2017 Update 4) no son archivos Dockerfile de varias fases.  Los pasos de estos archivos Dockerfile no compilan el código.  En su lugar, cuando Visual Studio compila un archivo Dockerfile de .NET Framework, primero compila el proyecto con MSBuild.  Cuando esto se realiza correctamente, Visual Studio compila el archivo Dockerfile, que simplemente copia la salida de la compilación de MSBuild en la imagen de Docker resultante.  Dado que los pasos para compilar el código no se incluyen en el archivo Dockerfile, no se puede compilar archivos Dockerfile de .NET Framework con `docker build` desde la línea de comandos. Debe utilizar MSBuild para compilar estos proyectos.

Para compilar una imagen para un solo proyecto de contenedor de Docker, puede usar MSBuild con la opción de comando `/t:ContainerBuild`. Por ejemplo:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Verá una salida similar a la que ve en la ventana **Output** cuando compila la solución desde el IDE de Visual Studio. Use siempre `/p:Configuration=Release`, ya que en los casos en los que Visual Studio usa la optimización de la compilación de varias fases, los resultados que se generan al compilar la configuración **Debug** podrían no ser los que se esperan. Vea [Depuración](#debugging).

Si usa un proyecto de Docker Compose, use el comando para compilar imágenes:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Preparación del proyecto

La *preparación del proyecto* se refiere a una serie de pasos que se producen cuando se selecciona el perfil de Docker de un proyecto (es decir, cuando se carga un proyecto o se agrega compatibilidad con Docker) con el fin de mejorar el rendimiento de las ejecuciones posteriores (**F5** o **Ctrl**+**F5**). Esto se puede configurar en **Herramientas** > **Opciones** > **Herramientas de contenedor**. Estas son las tareas que se ejecutan en segundo plano:

- Comprobar que Docker Desktop está instalado y en ejecución.
- Asegurarse de que Docker Desktop está establecido en el mismo sistema operativo que el proyecto.
- Extraer las imágenes de la primera fase del Dockerfile (la fase `base` en la mayoría de Dockerfiles).  
- Compilar el Dockerfile e iniciar el contenedor.

La preparación solo se produce en el modo **Rápido**, por lo que el contenedor en ejecución tiene el volumen de la carpeta de la aplicación montado. Esto significa que cualquier cambio en la aplicación no debe invalidar el contenedor. Esto mejora considerablemente el rendimiento de depuración y reduce el tiempo de espera de las tareas de larga duración, como la extracción de imágenes de gran tamaño.

## <a name="volume-mapping"></a>Asignación de volúmenes

Para que la depuración funcione en contenedores, Visual Studio usa la asignación de volúmenes a fin de asignar el depurador y las carpetas de NuGet desde el equipo host. Estos son los volúmenes que se montan en el contenedor:

|||
|-|-|
| **Depurador remoto** | Contiene los bits necesarios para ejecutar el depurador en el contenedor en función del tipo de proyecto. Esto se explica más |detalladamente en la sección [Depuración](#debugging).
| **Carpeta de la aplicación** | Contiene la carpeta del proyecto donde se encuentra el Dockerfile.|
| **Carpeta de origen** | Contiene el contexto de compilación que se pasa a los comandos de Docker.|
| **Carpetas de paquetes NuGet** | Contienen los paquetes NuGet y las carpetas de reserva que se leen desde el archivo *obj\{project}.csproj.nuget.g.props* del proyecto. |

En el caso de las aplicaciones web ASP.NET Core, puede haber dos carpetas adicionales para el certificado SSL y los secretos de usuario, lo que se explica con más detalle en la sección siguiente.

## <a name="ssl-enabled-aspnet-core-apps"></a>Aplicaciones ASP.NET Core habilitadas para SSL

Las herramientas de contenedor de Visual Studio admiten la depuración de una aplicación ASP.NET Core habilitada para SSL con un certificado de desarrollo, de la misma manera que cabría esperar que funcionase sin contenedores. Para que esto suceda, Visual Studio agrega un par de pasos más para exportar el certificado y ponerlo a disposición del contenedor. Este es el flujo:

1. Asegúrese de que el certificado de desarrollo local esté presente y sea de confianza en el equipo host mediante la herramienta `dev-certs`.
2. Exporte el certificado a %APPDATA%\ASP.NET\Https con una contraseña segura que esté almacenada en el almacén de secretos de usuario de esta aplicación en concreto.
3. Monte el volumen en los directorios siguientes:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core busca un certificado que coincida con el nombre de ensamblado de la carpeta *Https*, que es el motivo por el que se asigna al contenedor en esa ruta de acceso. La ruta de acceso del certificado y la contraseña pueden definirse alternativamente mediante variables de entorno (es decir, `ASPNETCORE_Kestrel__Certificates__Default__Path` y `ASPNETCORE_Kestrel__Certificates__Default__Password`) o en el archivo json de secretos de usuario, por ejemplo:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Para obtener más información sobre el uso de SSL con aplicaciones ASP.NET Core en contenedores, vea [Hospedaje de imágenes de ASP.NET Core con Docker a través de HTTPS](https://docs.microsoft.com/aspnet/core/security/docker-https).

## <a name="debugging"></a>Depuración

Al compilar en la configuración **Depuración**, varias de las optimizaciones que realiza Visual Studio ayudan con el rendimiento del proceso de compilación para proyectos en contenedores. El proceso de compilación de aplicaciones en contenedores no es tan sencillo como seguir los pasos descritos en el Dockerfile. La compilación en un contenedor es mucho más lenta que la compilación en el equipo local.  Por lo tanto, al compilar en la configuración **Debug**, Visual Studio compila los proyectos en el equipo local y, a continuación, comparte la carpeta de salida con el contenedor mediante el montaje del volumen. Una compilación con esta optimización habilitada se denomina compilación en modo *rápido*.

En modo **rápido**, Visual Studio llama a `docker build` con un argumento que le indica a Docker que compile solo la fase `base`.  Visual Studio controla el resto del proceso sin tener en cuenta el contenido de Dockerfile. Por lo tanto, cuando modifique el archivo Dockerfile, como para personalizar el entorno del contenedor o instalar dependencias adicionales, debe colocar las modificaciones en la primera fase.  No se ejecutará ningún paso personalizado colocado en las fases `build`, `publish` o `final` del archivo Dockerfile.

Esta optimización del rendimiento solo se produce cuando compila en la configuración **Debug**. En la configuración **Release**, la compilación se produce en el contenedor tal y como se especifica en el archivo Dockerfile.

Si desea deshabilitar la optimización del rendimiento y compilar como se especifica en el archivo Dockerfile, establezca la propiedad **ContainerDevelopmentMode** en **Regular** en el archivo del proyecto de la siguiente manera:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Para restaurar la optimización del rendimiento, quite la propiedad del archivo de proyecto.

 Cuando se inicia la depuración (**F5**), se vuelve a usar un contenedor iniciado previamente, si es posible. Si no desea volver a usar el contenedor anterior, puede usar los comandos **Rebuild** o **Clean** en Visual Studio para obligar a Visual Studio a usar un nuevo contenedor.

El proceso de ejecución del depurador depende del tipo de proyecto y del sistema operativo del contenedor:

|||
|-|-|
| **Aplicaciones .NET Core (contenedores de Linux)**| Visual Studio descarga `vsdbg` y lo asigna al contenedor, después se llama con el programa y los argumentos (es decir, `dotnet webapp.dll`) y luego el depurador se asocia al proceso. |
| **Aplicaciones .NET Core (contenedores de Windows)**| Visual Studio usa `onecoremsvsmon` y lo asigna al contenedor, lo ejecuta como punto de entrada y luego Visual Studio se conecta a él y se asocia al programa. Es similar a como normalmente se configuraría la depuración remota en otro equipo o máquina virtual.|
| **Aplicaciones .NET Framework** | Visual Studio usa `msvsmon` y lo asigna al contenedor, lo ejecuta como parte del punto de entrada, donde Visual Studio se puede conectar a él, y se asocia al programa.|

Para obtener información sobre `vsdbg.exe`, vea [Depuración fuera de ruta de .NET Core en Linux y OSX desde Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Punto de entrada de contenedor

Visual Studio usa un punto de entrada de contenedor personalizado en función del tipo de proyecto y del sistema operativo del contenedor; estas son las diferentes combinaciones:

|||
|-|-|
| **Contenedores de Linux** | El punto de entrada es `tail -f /dev/null`, que es una espera infinita para mantener el contenedor en ejecución. Cuando la aplicación se inicia a través del depurador, este es el responsable de ejecutar la aplicación (es decir, `dotnet webapp.dll`). Si se inicia sin depurar, las herramientas ejecutan `docker exec -i {containerId} dotnet webapp.dll` para ejecutar la aplicación.|
| **Contenedores de Windows**| El punto de entrada es algo como `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus`, que ejecuta el depurador, así que escucha para detectar conexiones. Cuando se inicia sin depurar, el depurador ejecuta la aplicación y un comando `docker exec`. En aplicaciones web .NET Framework, el punto de entrada es ligeramente diferente donde se agrega `ServiceMonitor` al comando.|

El punto de entrada de contenedor solo puede modificarse en proyectos de Docker Compose, no en proyectos de un solo contenedor.

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo personalizar aún más las compilaciones estableciendo propiedades de MSBuild adicionales en los archivos del proyecto. Consulte [Propiedades de MSBuild para proyectos en contenedores](container-msbuild-properties.md).

## <a name="see-also"></a>Vea también

[MSBuild](../msbuild/msbuild.md)
[Dockerfile en Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Contenedores de Linux en Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
