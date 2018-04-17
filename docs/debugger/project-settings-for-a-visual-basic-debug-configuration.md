---
title: Configuración para una configuración de depuración de Visual Basic del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 727e36da37c38d57013071d1d5013c27b8a95b87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Configuración del proyecto para una configuración de depuración de Visual Basic
Puede cambiar la configuración del proyecto para una [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] configuración de depuración en el **páginas de propiedades** ventana, como se describe en [configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). Las siguientes tablas muestran dónde encontrar valores relacionados con el depurador en el **páginas de propiedades** ventana.  
  
> [!WARNING]
>  Este tema no se aplica a las aplicaciones de UWP. Vea [inicie una sesión de depuración (VB, C#, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Ficha Depurar  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Configuración**|Establece el modo para compilar la aplicación. Elija entre **activo (depurar)**, **depurar**, **versión**, **todas las configuraciones de**.|  
|**Acción de inicio**|Este grupo de controles especifica la acción que se produce cuando se elige Inicio en el menú Depurar.<br /><br /> -   **Iniciar proyecto** es el valor predeterminado y lanza el proyecto de inicio para la depuración. <br />-   **Programa externo de inicio** permite iniciar y asociar un programa que no forma parte de un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Iniciar explorador con la dirección URL** le permite depurar una aplicación Web.|  
|**Argumentos de línea de comandos**|Especifica los argumentos de la línea de comandos para el programa que se va a depurar. El nombre de comando es el nombre del programa especificado en Programa externo de inicio. Si Acción de inicio se establece en Dirección URL de inicio, se omiten los argumentos de la línea de comandos.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se depura. En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación. El directorio de trabajo predeterminado es \bin\Debug o \bin\Release, dependiendo de la configuración actual.|  
|**Usar equipo remoto**|Cuando esta casilla está activada, se habilita la depuración remota. En el cuadro de texto, puede escribir el nombre de un equipo remoto donde se ejecutará la aplicación para depurarla o un [nombre de servidor Msvsmon](../debugger/remote-debugging.md). La ubicación del archivo EXE en el equipo remoto se especifica mediante la propiedad Ruta de acceso de los resultados, en la pestaña Compilar. La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.|  
|**Depuración de código no administrado**|Permite depurar llamadas a código nativo Win32 (no administrado) desde una aplicación administrada. Esto tiene el mismo efecto que seleccionar Mixto para Tipo de depurador en un proyecto de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].|  
|**Depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Ficha Compilar: presione el botón Opciones de compilación avanzadas  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Habilitar optimizaciones**|Se debe desactivar esta opción. La optimización hace que el código ejecutado sea diferente del código fuente que se ve en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], lo cual dificulta la depuración. Si se optimiza el código, los símbolos no se cargan de manera predeterminada al depurar con Sólo mi código.|  
|**Generar información de depuración**|Esta opción de configuración (equivalente a la opción /debug compiler), que está definida de manera predeterminada en las versiones de lanzamiento y de depuración, crea información de depuración en tiempo de generación. El depurador utiliza esta información para mostrar nombres de variables y otra información en formato útil durante la depuración. Si compila el programa sin esta información, la funcionalidad del depurador será limitada. Para obtener más información, consulte [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|**Definir constante DEBUG**|Definición de este símbolo permite la compilación condicional de funciones de salida de la [Debug (clase)](/dotnet/api/system.diagnostics.debug). Con la definición de este símbolo, los métodos de clase Debug generan resultados en la [resultados (ventana)](../ide/reference/output-window.md). Sin este símbolo, los métodos de la clase Debug no se compilan y no se generan resultados. Este símbolo debe definirse en la versión de depuración, no en la versión de lanzamiento. La definición de este símbolo en una versión de lanzamiento crea código innecesario que ralentiza la ejecución del programa.|  
|**Definir constante TRACE**|Definición de este símbolo permite la compilación condicional de funciones de salida de la [Trace (clase)](/dotnet/api/system.diagnostics.trace.aspx). Con la definición de este símbolo, los métodos de clase Trace generan resultados en la [resultados (ventana)](../ide/reference/output-window.md). Sin este símbolo, los métodos de la clase Trace no se compilan y no se generan resultados de seguimiento. Este símbolo se define de manera predeterminada para las versiones de lanzamiento y de depuración.|  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)