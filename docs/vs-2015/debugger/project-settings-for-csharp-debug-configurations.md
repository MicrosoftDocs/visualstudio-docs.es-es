---
title: Configuración del proyecto para las configuraciones de depuración de C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f1ec1c18fe92409a72994e4544215da01325d209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687515"
---
# <a name="project-settings-for--c-debug-configurations"></a>Configuración del proyecto para configuraciones de depuración en C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede cambiar la configuración del proyecto para una configuración de depuración de C# en la ventana **páginas de propiedades** , como se describe en [configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). En las siguientes tablas se muestra dónde encontrar valores relacionados con el depurador en la ventana **Páginas de propiedades**.  
  
> [!WARNING]
> Este tema no se aplica a las aplicaciones de la Tienda Windows. Vea [Iniciar una sesión de depuración (VB, C#, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
## <a name="debug-tab"></a><a name="BKMK_Debug_tab"></a> Pestaña depurar  
  
|**Configuración**|**Descripción**|  
|-----------------|---------------------|  
|**Configuración**|Establece el modo para compilar la aplicación. Puede elegir entre **Activo (Depurar)** , **Depurar**, **Liberar** y **Todas las configuraciones**.|  
|**Acción de inicio**|Este grupo de controles especifica la acción que se produce cuando se elige Inicio en el menú Depurar.<br /><br /> -   **Proyecto de inicio** es el valor predeterminado y lanza el proyecto de inicio para la depuración. Para obtener más información, vea [elegir el proyecto de inicio](https://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Programa externo de inicio** permite iniciar y asociar un programa que no forma parte de un proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, vea [asociar a un programa en ejecución](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Iniciar explorador en la dirección URL** permite depurar una aplicación web.|  
|**Argumentos de la línea de comandos**|Especifica los argumentos de la línea de comandos para el programa que se va a depurar. El nombre de comando es el nombre del programa especificado en Programa externo de inicio. Si Acción de inicio se establece en Dirección URL de inicio, los argumentos de la línea de comandos no se pueden especificar.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se depura. En [!INCLUDE[csprcs](../includes/csprcs-md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación: \bin\debug de manera predeterminada.|  
|**Usar máquina remota**|El nombre de un equipo remoto en el que se ejecutará la aplicación para la depuración o un [nombre de servidor de msvsmon](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). La ubicación del archivo EXE en el equipo remoto se especifica mediante la propiedad Ruta de acceso de los resultados de la carpeta Propiedades de configuración de la categoría Compilar. La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.|  
|**Habilitar depuración de código no administrado**|Permite depurar llamadas a código nativo Win32 (no administrado) desde una aplicación administrada.|  
|**Habilitar depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
  
## <a name="build-tab"></a><a name="BKMK_Build_tab"></a> Pestaña compilar  
  
|Configuración|Descripción|  
|-------------|-----------------|  
|**Símbolos de compilación condicional:**|A continuación se definen las constantes DEBUG y TRACE.<br /><br /> Estas constantes permiten la compilación condicional de [Debug (clase)](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) y [Trace (clase)](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Con la definición de estas constantes, los métodos de clase Debug y Trace generan resultados en la [ventana Salida](../ide/reference/output-window.md). Sin estas constantes, los métodos de clase Debug y Trace no se compilan y no se generan resultados.<br /><br /> -Debug se define normalmente en la versión de depuración de un programa y sin definir en la versión de lanzamiento.<br />-El seguimiento se define normalmente en las versiones de depuración y lanzamiento.|  
|**Optimizar código**|A menos que encuentre un error que sólo aparece en código optimizado, debe dejar esta configuración desactivada en la versión de depuración. El código optimizado es más difícil de depurar, puesto que las instrucciones no se corresponden directamente con las instrucciones de las ventanas de código fuente.|  
|**Ruta de acceso de salida:**|Normalmente se establece en bin\Debug para la depuración.|  
  
## <a name="see-also"></a>Consulte también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
