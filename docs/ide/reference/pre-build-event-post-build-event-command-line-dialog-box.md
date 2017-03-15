---
title: "L&#237;nea de comandos del evento anterior/posterior a la compilaci&#243;n (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEventsBuilder"
  - "vb.ProjectPropertiesBuildEventsBuilder"
helpviewer_keywords: 
  - "$(SolutionExt)"
  - "$(ProjectDir)"
  - "$(TargetPath)"
  - "$(ProjectExt)"
  - "$(TargetFileName)"
  - "$(PlatformName)"
  - "$(SolutionName)"
  - "macros, eventos de compilación"
  - "$(SolutionPath)"
  - "$(ProjectPath)"
  - "$(ProjectFileName)"
  - "$(DevEnvDir)"
  - "$(TargetName)"
  - "$(TargetDir)"
  - "$(SolutionDir)"
  - "$(TargetExt)"
  - "$(OutDir)"
  - "$(ConfigurationName)"
  - "$(SolutionFileName)"
  - "$(ProjectName)"
  - "eventos de compilación, macros"
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# L&#237;nea de comandos del evento anterior/posterior a la compilaci&#243;n (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede escribir eventos anteriores o posteriores a la compilación para el [Eventos de compilación \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md) directamente en el cuadro de edición, o puede seleccionar macros anteriores o posteriores a la generación a partir de una lista de macros disponibles.  
  
> [!NOTE]
>  Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.  
  
## Lista de elementos de la interfaz de usuario  
 **Cuadro de edición de la línea de comandos**  
 Contiene los eventos que se van a ejecutar, ya sean anteriores o posteriores a la compilación.  
  
> [!NOTE]
>  Agregue una instrucción `call` delante de todos los comandos posteriores a la compilación que ejecutan archivos .bat.  Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Macros**  
 Expande el cuadro de edición para mostrar una lista de macros que se insertan en el cuadro de edición de la línea de comandos.  
  
 **Tabla de macros**  
 Muestra las macros disponibles y su valor.  Vea Macros a continuación para obtener una descripción de cada una.  Sólo puede seleccionar una macro cada vez para insertarla en el cuadro de edición de la línea de comandos.  
  
 **Insert**  
 Inserta en el cuadro de edición de la línea de comandos la macro seleccionada en la tabla de macros.  
  
### Macros  
 Puede utilizar cualquiera de estas macros para especificar ubicaciones de archivos u obtener el nombre real del archivo de entrada en caso de que haya varias selecciones.  Estas macros no hacen distinción entre mayúsculas y minúsculas.  
  
|Macro|Descripción|  
|-----------|-----------------|  
|`$(ConfigurationName)`|Nombre de la configuración del proyecto actual \(por ejemplo, "Versión de depuración"\).|  
|`$(OutDir)`|Ruta de acceso \(relativa al directorio del proyecto\) al directorio de archivos de salida.  Se resuelve en el valor de la propiedad Directorio de resultados.  Incluye la barra diagonal inversa final '\\'.|  
|`$(DevEnvDir)`|El directorio de instalación de Visual Studio \(definido con la unidad y la ruta de acceso\); incluye “\\”\) final de barra diagonal inversa.|  
|`$(PlatformName)`|Nombre de la plataforma de destino actual.  Por ejemplo, "CualquierCPU".|  
|`$(ProjectDir)`|Directorio del proyecto \(definido con unidad y ruta de acceso\); incluye la barra diagonal inversa \('\\'\) final.|  
|`$(ProjectPath)`|Nombre de la ruta de acceso absoluta del proyecto \(definido con unidad, ruta de acceso, nombre base y extensión de archivo\).|  
|`$(ProjectName)`|Nombre base del proyecto.|  
|`$(ProjectFileName)`|Nombre de archivo del proyecto \(definido con nombre base y extensión de archivo\).|  
|`$(ProjectExt)`|Extensión de archivo del proyecto.  Incluye un '.' antes de la extensión de archivo.|  
|`$(SolutionDir)`|Directorio de la solución \(definido con unidad y ruta de acceso\); incluye la barra diagonal inversa \('\\'\) final.|  
|`$(SolutionPath)`|Nombre de la ruta de acceso absoluta de la solución \(definido con unidad, ruta de acceso, nombre base y extensión de archivo\).|  
|`$(SolutionName)`|Nombre base de la solución.|  
|`$(SolutionFileName)`|Nombre de archivo de la solución \(definido con nombre base y extensión de archivo\).|  
|`$(SolutionExt)`|Extensión de archivo de la solución.  Incluye un '.' antes de la extensión de archivo.|  
|`$(TargetDir)`|Directorio del archivo de salida principal de la compilación \(definido con unidad y ruta de acceso\).  Incluye la barra diagonal inversa final '\\'.|  
|`$(TargetPath)`|Nombre de la ruta de acceso absoluta del archivo de salida principal de la compilación \(definido con unidad, ruta de acceso, nombre base y extensión de archivo\).|  
|`$(TargetName)`|Nombre base del archivo de salida principal de la compilación.|  
|`$(TargetFileName)`|Nombre del archivo de salida principal de la compilación \(definido con nombre base y extensión de archivo\).|  
|`$(TargetExt)`|Extensión de archivo del archivo de salida principal de la compilación.  Incluye un '.' antes de la extensión de archivo.|  
  
## Vea también  
 [Especificar eventos de compilación personalizados en Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [Eventos de compilación \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [Cómo: Especificar eventos de compilación \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Cómo: Especificar eventos de compilación \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)