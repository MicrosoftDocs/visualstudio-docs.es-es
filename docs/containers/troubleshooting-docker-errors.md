---
title: Solución de problemas de errores del cliente Docker en Windows | Microsoft Docs
description: Solucione los problemas que encuentre al usar Visual Studio para crear e implementar aplicaciones web en Docker en Windows mediante Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: f16ecd899bc1dddd7383ef1a815ed6197b799a19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859533"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Solución de problemas de desarrollo de Visual Studio con Docker

Al trabajar con las herramientas de contenedor de Visual Studio, se pueden producir problemas al compilar o depurar la aplicación. A continuación, se especifican algunos pasos comunes de solución de problemas.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>El uso compartido de volúmenes no está habilitado. Habilite el uso compartido de volúmenes en la configuración de Docker CE para Windows (solo en contenedores con Linux)

El uso compartido de archivos solo necesita administrarse si usa Hyper-V con Docker. Si usa WSL 2, los siguientes pasos no son necesarios y la opción de uso compartido de archivos no estará visible. Para resolver este problema, haga lo siguiente:

1. Haga clic derecho en **Docker para Windows** en el área de notificación y, a continuación, seleccione **Configuración**.
1. Seleccione **Recursos** > **Uso compartido de archivos** y comparta la carpeta a la que se necesita tener acceso. Es posible compartir toda la unidad del sistema, pero no se recomienda.

    ![unidades compartidas](media/troubleshooting-docker-errors/docker-settings-image.png)

> [!TIP]
> Las versiones de Visual Studio posteriores a la versión 15.6 de Visual Studio 2017 le avisarán si las **unidades compartidas** no están configuradas.

## <a name="unable-to-start-debugging"></a>No se puede iniciar la depuración

Una razón podría estar relacionada con tener componentes de depuración obsoletos en la carpeta del perfil del usuario. Ejecute los comandos siguientes para quitar estas carpetas, a fin de que se descarguen los últimos componentes de depuración en la siguiente sesión de depuración.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Errores específicos de redes al depurar una aplicación

Intente ejecutar el script que puede descargar de [Cleanup Container Host Networking](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking) (Limpieza de redes host de contenedores), que actualizará los componentes de red en el equipo host.

## <a name="mounts-denied"></a>Montajes denegados

Al usar Docker para macOS, podría encontrar un error que haga referencia a la carpeta /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Agregue la carpeta a la pestaña Uso compartido de archivos de Docker.

## <a name="docker-users-group"></a>Grupo de usuarios de Docker

Podría aparecer el siguiente error en Visual Studio al trabajar con contenedores:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Debe ser miembro del grupo "docker-users" para obtener permisos para trabajar con contenedores de Docker.  Para agregarse al grupo en Windows 10, siga estos pasos:

1. En el menú Inicio, abra **Administración de equipos**.
1. Expanda **Grupos y usuarios locales** y seleccione **Grupos**.
1. Busque el grupo **docker-users**, haga clic con el botón derecho y seleccione **Agregar a grupo**.
1. Agregue la cuenta o cuentas de usuario.
1. Cierre la sesión y vuelva a iniciarla para que estos cambios surtan efecto.

También puede usar el comando `net localgroup` en el símbolo del sistema del administrador para agregar usuarios a grupos determinados.

```cmd
net localgroup docker-users DOMAIN\username /add
```

En PowerShell, use la función [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember).

## <a name="low-disk-space"></a>Espacio de disco bajo

De forma predeterminada, Docker almacena imágenes en la carpeta *%ProgramData%/Docker/* , que normalmente se encuentra en la unidad del sistema, *C:\ProgramData\Docker\*. Para evitar que las imágenes ocupen espacio valioso en la unidad del sistema, puede cambiar la ubicación de la carpeta de imágenes. Para ello:

 1. Haga clic con el botón derecho en el icono de Docker en la barra de tareas y seleccione **Configuración**.
 1. Seleccione **Docker Engine** (Motor de Docker). 
 1. En el panel de edición, agregue la configuración de la propiedad `graph` con el valor de la ubicación deseada para las imágenes de Docker:

```json
    "graph": "D:\\mypath\\images"
```

![Captura de pantalla del uso compartido de archivos de Docker.](media/troubleshooting-docker-errors/docker-daemon-settings.png)

Haga clic en **Apply & Restart** (Aplicar y reiniciar). En estos pasos se modifica el archivo de configuración que se encuentra en *%ProgramData%\docker\config\daemon.json*. Las imágenes compiladas previamente no se mueven.

## <a name="container-type-mismatch"></a>Error de coincidencia de tipos de contenedores

Al agregar compatibilidad con Docker a un proyecto, se elige un contenedor de Linux o Windows. Si el host de servidor de Docker no está configurado para ejecutar el mismo tipo de contenedor que el destino del proyecto, es probable que vea un error parecido al siguiente:

![Captura de pantalla del error de coincidencia entre el host y el proyecto de Docker.](media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png)

Para solucionar este problema:

- Haga clic con el botón derecho en el icono de Docker para Windows en la bandeja del sistema y elija **Switch to Linux containers…** (Cambiar a contenedores de Linux…) o **Switch to Windows containers…** (Cambiar a contenedores de Windows…).

## <a name="microsoftdockertools-github-repo"></a>Repositorio de GitHub de Microsoft/DockerTools

Para otros problemas que detecte, consulte los problemas de [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).

## <a name="see-also"></a>Consulte también

- [Solucionar problemas de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
