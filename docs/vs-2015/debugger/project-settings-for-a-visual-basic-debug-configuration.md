---
title: Configuración de proyectos para una configuración de depuración de Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af9d9976c6aa6743cfda4c69d3b2f8d958ab03bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575519"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Configuración del proyecto para una configuración de depuración de Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [configuración del proyecto para una configuración de depuración de Visual Basic](https://docs.microsoft.com/visualstudio/debugger/project-settings-for-a-visual-basic-debug-configuration).  
  
Puede cambiar la configuración del proyecto para una [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] configuración de depuración en el **páginas de propiedades** ventana, como se describe en [configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). En las tablas siguientes se muestran dónde encontrar valores relacionados con el depurador en el **páginas de propiedades** ventana.  
  
> [!WARNING]
>  Este tema no se aplica a las aplicaciones de la Tienda. Consulte [iniciar una sesión de depuración (VB, C#, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Ficha Depurar  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Configuración**|Establece el modo para compilar la aplicación. Elija entre **activo (depurar)**, **depurar**, **versión**, **todas las configuraciones de**.|  
|**Acción de inicio**|Este grupo de controles especifica la acción que se produce cuando se elige Inicio en el menú Depurar.<br /><br /> -   **Iniciar proyecto** es el valor predeterminado y lanza el proyecto de inicio para la depuración. Para obtener más información, consulte [Cómo: Establecer proyectos de inicio](http://msdn.microsoft.com/en-us/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Iniciar programa externo** le permite iniciar y asociar a un programa que no es parte de un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyecto. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Iniciar explorador con la dirección URL** le permite depurar una aplicación Web.|  
|**Argumentos de línea de comandos**|Especifica los argumentos de la línea de comandos para el programa que se va a depurar. El nombre de comando es el nombre del programa especificado en Programa externo de inicio. Si Acción de inicio se establece en Dirección URL de inicio, se omiten los argumentos de la línea de comandos.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se depura. En [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación. El directorio de trabajo predeterminado es \bin\Debug o \bin\Release, dependiendo de la configuración actual.|  
|**Usar equipo remoto**|Cuando esta casilla está activada, se habilita la depuración remota. En el cuadro de texto, puede escribir el nombre de un equipo remoto donde se ejecutará la aplicación con fines de depuración o un [nombre de servidor Msvsmon](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). La ubicación del archivo EXE en el equipo remoto se especifica mediante la propiedad Ruta de acceso de los resultados, en la pestaña Compilar. La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.|  
|**Depuración de código no administrado**|Permite depurar llamadas a código nativo Win32 (no administrado) desde una aplicación administrada. Esto tiene el mismo efecto que seleccionar Mixto para Tipo de depurador en un proyecto de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].|  
|**Depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Ficha Compilar: presione el botón Opciones de compilación avanzadas  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Habilitar optimizaciones**|Se debe desactivar esta opción. La optimización hace que el código ejecutado sea diferente del código fuente que se ve en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lo cual dificulta la depuración. Si se optimiza el código, los símbolos no se cargan de manera predeterminada al depurar con Sólo mi código.|  
|**Generar información de depuración**|Esta opción de configuración (equivalente a la opción /debug compiler), que está definida de manera predeterminada en las versiones de lanzamiento y de depuración, crea información de depuración en tiempo de generación. El depurador utiliza esta información para mostrar nombres de variables y otra información en formato útil durante la depuración. Si compila el programa sin esta información, la funcionalidad del depurador será limitada. Para obtener más información, consulte [/debug](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Definir constante DEBUG**|Definición de este símbolo permite la compilación condicional de las funciones de salida desde el [Debug (clase)](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Con la definición de este símbolo, los métodos de clase Debug generan resultados en la [ventana de salida](../ide/reference/output-window.md). Sin este símbolo, los métodos de la clase Debug no se compilan y no se generan resultados. Este símbolo debe definirse en la versión de depuración, no en la versión de lanzamiento. La definición de este símbolo en una versión de lanzamiento crea código innecesario que ralentiza la ejecución del programa.|  
|**Definir constante TRACE**|Definición de este símbolo permite la compilación condicional de las funciones de salida desde el [Trace (clase)](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Con la definición de este símbolo, los métodos de la clase Trace generan resultados en la [ventana de salida](../ide/reference/output-window.md). Sin este símbolo, los métodos de la clase Trace no se compilan y no se generan resultados de seguimiento. Este símbolo se define de manera predeterminada para las versiones de lanzamiento y de depuración.|  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)



