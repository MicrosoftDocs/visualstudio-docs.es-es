---
title: "Configuraci&#243;n del proyecto para una configuraci&#243;n de depuraci&#243;n de Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbProjectPropertiesDebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "compilaciones de depuración, configuración del proyecto"
  - "configuraciones de depuración, Visual Basic"
  - "depurar [Visual Basic], configuración del depurador"
  - "configuraciones del proyecto, depuración"
  - "configuración de proyectos [Visual Studio], configuraciones de depuración"
  - "proyectos [Visual Studio], configuraciones de depuración"
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configuraci&#243;n del proyecto para una configuraci&#243;n de depuraci&#243;n de Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es posible cambiar la configuración del proyecto para una configuración de depuración de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en la ventana **Páginas de propiedades**, como se describe en [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  En las siguientes tablas se muestra dónde encontrar valores relacionados con el depurador en la ventana **Páginas de propiedades**.  
  
> [!WARNING]
>  Este tema no se aplica a las aplicaciones de la Tienda.  Vea [Iniciar una sesión de depuración \(VB, C\#, C\+\+ y XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
### Ficha Depurar  
  
|Configuración|Descripción|  
|-------------------|-----------------|  
|**Configuración**|Establece el modo para compilar la aplicación.  Puede elegir entre **Activo \(Depurar\)**, **Depurar**, **Liberar**, **Todas las config.**|  
|**Acción de inicio**|Este grupo de controles especifica la acción que se produce cuando se elige Inicio en el menú Depurar.<br /><br /> -   **Proyecto de inicio** es el valor predeterminado y lanza el proyecto de inicio para la depuración.  Para obtener más información, vea [Cómo: Establecer proyectos de inicio](http://msdn.microsoft.com/es-es/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Programa externo de inicio** permite iniciar y asociar un programa que no forma parte de un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obtener más información, vea [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Iniciar explorador con la dirección URL** permite depurar una aplicación web.|  
|**Argumentos de la línea de comandos**|Especifica los argumentos de la línea de comandos para el programa que se va a depurar.  El nombre de comando es el nombre del programa especificado en Programa externo de inicio.  Si Acción de inicio se establece en Dirección URL de inicio, se omiten los argumentos de la línea de comandos.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se depura.  En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación.  El directorio de trabajo predeterminado es \\bin\\Debug o \\bin\\Release, dependiendo de la configuración actual.|  
|**Usar equipo remoto**|Cuando esta casilla está activada, se habilita la depuración remota.  En el cuadro de texto escriba el nombre del equipo remoto en el que se ejecutará la aplicación para depurarla o un [Nombre de servidor Msvsmon](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  La ubicación del archivo EXE en el equipo remoto se especifica mediante la propiedad Ruta de acceso de los resultados, en la pestaña Compilar.  La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.|  
|**Depuración de código no administrado**|Permite depurar llamadas a código nativo Win32 \(no administrado\) desde una aplicación administrada.  Esto tiene el mismo efecto que seleccionar Mixto para Tipo de depurador en un proyecto de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].|  
|**Depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
  
### Ficha Compilar: presione el botón Opciones de compilación avanzadas  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**Habilitar optimizaciones**|Se debe desactivar esta opción.  La optimización hace que el código ejecutado sea diferente del código fuente que se ve en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], lo cual dificulta la depuración.  Si se optimiza el código, los símbolos no se cargan de manera predeterminada al depurar con Sólo mi código.|  
|**Generar información de depuración**|Esta opción de configuración \(equivalente a la opción \/debug compiler\), que está definida de manera predeterminada en las versiones de lanzamiento y de depuración, crea información de depuración en tiempo de generación.  El depurador utiliza esta información para mostrar nombres de variables y otra información en formato útil durante la depuración.  Si compila el programa sin esta información, la funcionalidad del depurador será limitada.  Para obtener más información, vea [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|**Definir constante DEBUG**|La definición de este símbolo permite la compilación condicional de las funciones de resultados de [Debug \(Clase\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx).  Con la definición de este símbolo, los métodos de la clase Debug generan resultados en [Salida \(Ventana\)](../ide/reference/output-window.md).  Sin este símbolo, los métodos de la clase Debug no se compilan y no se generan resultados.  Este símbolo debe definirse en la versión de depuración, no en la versión de lanzamiento.  La definición de este símbolo en una versión de lanzamiento crea código innecesario que ralentiza la ejecución del programa.|  
|**Definir constante TRACE**|La definición de este símbolo permite la compilación condicional de las funciones de resultados de [Trace \(Clase\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx).  Con la definición de este símbolo, los métodos de la clase Trace generan resultados en [Salida \(Ventana\)](../ide/reference/output-window.md).  Sin este símbolo, los métodos de la clase Trace no se compilan y no se generan resultados de seguimiento.  Este símbolo se define de manera predeterminada para las versiones de lanzamiento y de depuración.|  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)