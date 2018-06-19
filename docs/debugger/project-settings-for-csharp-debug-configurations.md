---
title: Configuración para configuraciones de depuración de C# del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 65b30c1dc0b4306c7104b4d0b3dcd38a2cc55b1d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478332"
---
# <a name="project-settings-for--c-debug-configurations"></a>Configuración del proyecto para configuraciones de depuración en C#
Puede cambiar la configuración del proyecto para una configuración de depuración de C# en el **páginas de propiedades** ventana, como se describe en [configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). Las siguientes tablas muestran dónde encontrar valores relacionados con el depurador en el **páginas de propiedades** ventana.  
  
> [!WARNING]
>  Este tema no se aplica a las aplicaciones de UWP. Vea [inicie una sesión de depuración (VB, C#, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Ficha Depurar  
  
|**Configuración de**|**Descripción**|  
|-----------------|---------------------|  
|**Configuración**|Establece el modo para compilar la aplicación. Elija entre **activo (depurar)**, **depurar**, **versión**, **todas las configuraciones de**.|  
|**Acción de inicio**|Este grupo de controles especifica la acción que se produce cuando se elige Inicio en el menú Depurar.<br /><br /> -   **Iniciar proyecto** es el valor predeterminado y lanza el proyecto de inicio para la depuración. Para obtener más información, consulte [elegir el proyecto de inicio](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Programa externo de inicio** permite iniciar y asociar un programa que no forma parte de un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Para obtener más información, consulte [adjuntar a un programa en ejecución](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Iniciar explorador con la dirección URL** le permite depurar una aplicación Web.|  
|**Argumentos de la línea de comandos**|Especifica los argumentos de la línea de comandos para el programa que se va a depurar. El nombre de comando es el nombre del programa especificado en Programa externo de inicio. Si Acción de inicio se establece en Dirección URL de inicio, los argumentos de la línea de comandos no se pueden especificar.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se depura. En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación: \bin\debug de manera predeterminada.|  
|**Usar máquina remota**|El nombre de un equipo remoto donde se ejecutará la aplicación para depurarla o un [nombre de servidor Msvsmon](../debugger/remote-debugging.md). La ubicación del archivo EXE en el equipo remoto se especifica mediante la propiedad Ruta de acceso de los resultados de la carpeta Propiedades de configuración de la categoría Compilar. La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.|
|**Habilitar depuración de código no administrado**|Permite depurar llamadas a código nativo Win32 (no administrado) desde una aplicación administrada.|  
|**Habilitar depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Generar (ficha)  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Símbolos de compilación condicional:**|A continuación se definen las constantes DEBUG y TRACE.<br /><br /> Estas constantes permiten la compilación condicional de la [Debug (clase)](/dotnet/api/system.diagnostics.debug) y [Trace (clase)](/dotnet/api/system.diagnostics.trace). Con la definición de estas constantes, depurar y métodos de clase Trace generan resultados en la [resultados (ventana)](../ide/reference/output-window.md). Sin estas constantes, los métodos de clase Debug y Trace no se compilan y no se generan resultados.<br /><br /> -Debug normalmente se define en la versión de depuración de un programa y no definido en la versión de lanzamiento.<br />-Trace se define normalmente en versiones de lanzamiento y depuración.|  
|**Optimizar código**|A menos que encuentre un error que sólo aparece en código optimizado, debe dejar esta configuración desactivada en la versión de depuración. El código optimizado es más difícil de depurar, puesto que las instrucciones no se corresponden directamente con las instrucciones de las ventanas de código fuente.|  
|**Ruta de acceso de salida:**|Normalmente se establece en bin\Debug para la depuración.|

> [!NOTE]
> Para obtener más información sobre las opciones de depuración que aparecen en la **avanzadas** botón, consulte [cuadro de diálogo de configuración de compilación avanzada (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). El formato portable para archivos de símbolos (.pdb) es el formato más reciente de multiplataforma para .NET Core. 
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)