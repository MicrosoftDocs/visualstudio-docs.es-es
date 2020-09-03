---
title: Compatibilidad con launchSettings.json
description: Este documento describe la compatibilidad de launchSettings.json en Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247932"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Al desarrollar proyectos de ASP.NET Core, puede configurar cómo se debe iniciar el proyecto en los escenarios de desarrollo mediante la personalización del contenido del archivo. En Visual Studio para Mac, puede actualizar este archivo mediante la interfaz de usuario de opciones del proyecto o editando directamente el archivo. Este archivo es el mismo archivo de configuración que se puede usar al ejecutar Visual Studio en Windows o desde la línea de comandos con `dotnet`. Este archivo se almacena en el proyecto en la carpeta Propiedades.

Para más información, consulte [Usar varios entornos en ASP.NET Core](/aspnet/core/fundamentals/environments). En este artículo, trataremos cómo actualizar este archivo en Visual Studio para Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Actualización de la configuración de inicio mediante Visual Studio para Mac

Puede editar directamente el archivo launchSettings.json en Visual Studio para Mac o puede usar las opciones del proyecto para editarlo. Para acceder a las opciones del proyecto, haga clic con el botón derecho en el proyecto y seleccione **Opciones**.

![Menú contextual del proyecto con "Opciones" seleccionada](media/vsmac-ctx-proj-options.png)

Seleccione **Ejecutar** > **Configuraciones** > **Predeterminada**.

!["Ejecutar", "Configuraciones" y "Predeterminada" en las opciones del proyecto](media/vsmac-run-config-default.png)

Aquí configurará principalmente dos cosas:

- Variables de entorno
- Dirección URL de la aplicación del proyecto

## <a name="configure-environment-variables"></a>Configuración de las variables de entorno

Puede usar la cuadrícula para especificar los valores de las variables de entorno. Estas variables de entorno se establecerán al iniciar la aplicación en Visual Studio para Mac. Al desarrollar aplicaciones de ASP.NET Core, debe tener en cuenta la variable de entorno especial `ASPNETCORE_ENVIRONMENT`. Para obtener más información, consulte [Usar varios entornos en ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configuración de la dirección URL de inicio

Para configurar la dirección URL con la que se iniciará la aplicación, vaya a la pestaña **ASP.NET Core**.

![Dirección URL de la aplicación en las opciones del proyecto](media/vsmac-run-config-default-aspnetcore.png)

Aquí puede especificar la dirección URL que escuchará la aplicación cuando se inicie.
