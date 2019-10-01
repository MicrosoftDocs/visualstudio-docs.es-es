---
title: Compatibilidad con launchSettings.json
description: Este documento describe la compatibilidad de launchSettings.json en Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213820"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Al desarrollar proyectos de ASP.NET Core, puede personalizar el contenido del archivo `launchSettings.json` para configurar la manera en que se debe iniciar el proyecto en escenarios de desarrollo. En Visual Studio para Mac, puede actualizar este archivo mediante la interfaz de usuario de opciones del proyecto o editando directamente el archivo `launchSettings.json`. Este archivo es el mismo archivo de configuración que se puede usar al ejecutar Visual Studio en Windows o desde la línea de comandos con `dotnet`. Este archivo se almacena en el proyecto en la carpeta `Properties`.

Para obtener información más detallada, puede ir a [Usar varios entornos en ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). En este documento, trataremos cómo actualizar este archivo en Visual Studio para Mac.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Actualización de la configuración de inicio mediante Visual Studio para Mac

Puede editar directamente `launchSettings.json` en Visual Studio para Mac o puede usar las opciones del proyecto para editarlo. Para acceder a las opciones del proyecto, haga clic con el botón derecho en el proyecto y seleccione Opciones. Consulte la imagen que aparece a continuación.

![opciones del menú contextual del proyecto seleccionadas](media/vsmac-ctx-proj-options.png)

Cuando aparezca este cuadro de diálogo, vaya a Ejecutar > Configuraciones > Valor predeterminado.

![ejecutar configuraciones valor predeterminado](media/vsmac-run-config-default.png)

Básicamente hay dos cosas que configurará aquí.

 - Variables de entorno que se establecen en el inicio
 - Dirección URL de inicio del proyecto

## <a name="configure-environment-variables"></a>Configuración de las variables de entorno

Puede usar la cuadrícula para especificar los valores de las variables de entorno. Estas variables de entorno se establecerán al iniciar la aplicación en Visual Studio para Mac. Al desarrollar aplicaciones de ASP.NET Core, debe tener en cuenta la variable de entorno especial `ASPNETCORE_ENVIRONMENT`. Para obtener más información, consulte [Usar varios entornos en ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Configuración de la dirección URL de inicio

Para configurar la dirección URL en la que se iniciará la aplicación, vaya a la pestaña ASP.NET Core.

![opciones de proyecto url de inicio](media/vsmac-run-config-default-aspnetcore.png)

Aquí puede especificar las direcciones URL que la aplicación escuchará cuando se inicie.