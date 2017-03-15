---
title: "Configuraci&#243;n del proyecto para configuraciones de depuraci&#243;n en C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "compilaciones de depuración, configuración del proyecto"
  - "configuraciones de depuración, C#"
  - "configuraciones de depuración, J#"
  - "depurar [C#], configuración del depurador"
  - "depurar [J#], configuración del depurador"
  - "configuraciones del proyecto, depuración"
  - "configuración de proyectos [Visual Studio], configuraciones de depuración"
  - "proyectos [Visual Studio], configuraciones de depuración"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configuraci&#243;n del proyecto para configuraciones de depuraci&#243;n en C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es posible cambiar la configuración del proyecto para una configuración de depuración de C\# en la ventana **Páginas de propiedades**, como se describe en [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  En las siguientes tablas se muestra dónde encontrar valores relacionados con el depurador en la ventana **Páginas de propiedades**.  
  
> [!WARNING]
>  Este tema no se aplica a las aplicaciones de la Tienda Windows.  Consulte [Iniciar una sesión de depuración \(VB, C\#, C\+\+ y XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
##  <a name="BKMK_Debug_tab"></a> Ficha Depurar  
  
|**Configuración**|**Descripción**|  
|-----------------------|---------------------|  
|**Configuración**|Establece el modo para compilar la aplicación.  Puede elegir entre **Activo \(Depurar\)**, **Depurar**, **Liberar**, **Todas las config.**|  
|**Acción de inicio**|Este grupo de controles especifica la acción que se produce cuando se elige Inicio en el menú Depurar.<br /><br /> -   **Proyecto de inicio** es el valor predeterminado y lanza el proyecto de inicio para la depuración.  Para obtener más información, vea [Elegir el proyecto de inicio](http://msdn.microsoft.com/es-es/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Programa externo de inicio** permite iniciar y asociar un programa que no forma parte de un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obtener más información, vea [Asociar el depurador a un programa en ejecución](http://msdn.microsoft.com/es-es/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Iniciar explorador con la dirección URL** permite depurar una aplicación web.|  
|**Argumentos de la línea de comandos**|Especifica los argumentos de la línea de comandos para el programa que se va a depurar.  El nombre de comando es el nombre del programa especificado en Programa externo de inicio.  Si Acción de inicio se establece en Dirección URL de inicio, los argumentos de la línea de comandos no se pueden especificar.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se depura.  En [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], el directorio de trabajo es el directorio desde el que se inicia la aplicación: \\bin\\debug de manera predeterminada.|  
|**Usar equipo remoto**|El nombre de un equipo remoto donde se ejecutará la aplicación para su depuración o un [nombre de servidor Msvsmon](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  La ubicación del archivo EXE en el equipo remoto se especifica mediante la propiedad Ruta de acceso de los resultados de la carpeta Propiedades de configuración de la categoría Compilar.  La ubicación debe ser un directorio que se pueda compartir en el equipo remoto.|  
|**Habilitar depuración de código no administrado**|Permite depurar llamadas a código nativo Win32 \(no administrado\) desde una aplicación administrada.|  
|**Habilitar depuración de SQL Server**|Permite depurar objetos de la base de datos de SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Pestaña Compilar  
  
|Configuración|Descripción|  
|-------------------|-----------------|  
|**Símbolos de compilación condicional:**|A continuación se definen las constantes DEBUG y TRACE.<br /><br /> Estas constantes permiten la compilación condicional de [Debug \(clase\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) y [Trace \(clase\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx).  Con la definición de estas constantes, los métodos de clase Debug y Trace generan resultados en [Salida \(ventana\)](../ide/reference/output-window.md).  Sin estas constantes, los métodos de clase Debug y Trace no se compilan y no se generan resultados.<br /><br /> -   Normalmente Debug se define en la versión de depuración de un programa y no se define en la versión de lanzamiento.<br />-   El seguimiento se define normalmente en las versiones de depuración y liberación.|  
|**Optimizar código**|A menos que encuentre un error que sólo aparece en código optimizado, debe dejar esta configuración desactivada en la versión de depuración.  El código optimizado es más difícil de depurar, puesto que las instrucciones no se corresponden directamente con las instrucciones de las ventanas de código fuente.|  
|**Ruta de acceso de los resultados:**|Normalmente se establece en bin\\Debug para la depuración.|  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)