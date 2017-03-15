---
title: "RC (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), RC (tarea)"
  - "RC (tarea) (MSBuild (Visual C++))"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# RC (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Incluye la herramienta Compilador de recursos de Microsoft Windows, rc.exe.  La tarea **RC** compila recursos, como cursores, iconos, mapas de bits, cuadros de diálogo y fuentes, en un archivo de recursos \(.res\).  Para obtener más información, vea "Resource Compiler" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **RC** .  La mayoría de los parámetros de tarea, y algunos conjuntos de parámetros, corresponden a una opción de la línea de comandos.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parámetro **String\[\]** opcional.<br /><br /> Agrega un directorio a la lista de directorios en los que se buscan archivos de inclusión.<br /><br /> Para obtener más información, vea la opción **\/I** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones de línea de comandos, por ejemplo **"***\/opción1 \/opción2 \/opción \#*".  Utilice este parámetro para especificar opciones de la línea de comandos que no son representadas por ningún otro parámetro de tarea **RC**.<br /><br /> Para obtener más información, vea las opciones de [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.|  
|**Culture**|Parámetro **String** opcional.<br /><br /> Especifica un Id. de configuración regional que representa la referencia cultural utilizada en los recursos.<br /><br /> Para obtener más información, vea la opción **\/l** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.|  
|**IgnoreStandardIncludePath**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que el compilador de recursos compruebe la variable de entorno INCLUDE cuando busca archivos de encabezado o archivos de recursos.<br /><br /> Para obtener más información, vea la opción **\/x** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.|  
|**NullTerminateStrings**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, termina con un carácter null todas las cadenas de la tabla de cadenas.<br /><br /> Para obtener más información, vea la opción **\/n** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.|  
|**PreprocessorDefinitions**|Parámetro **String\[\]** opcional.<br /><br /> Defina uno o más símbolos del preprocesador para el compilador de recursos.  Especifique una lista de símbolos de macro.<br /><br /> Para obtener más información, vea la opción **\/d** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.  También vea **UndefinePreprocessorDefinitions** en esta tabla.|  
|**ResourceOutputFileName**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de recursos.  Especifique un nombre para el archivo de recursos.<br /><br /> Para obtener más información, vea la opción **\/fo** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.|  
|**ShowProgress**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, muestra mensajes que informan sobre el progreso del compilador.<br /><br /> Para obtener más información, vea la opción **\/v** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.|  
|**Source**|Parámetro `ITaskItem[]` requerido.<br /><br /> Define una matriz de elementos de archivo de origen de MSBuild que las tareas pueden usar y emitir.|  
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita la presentación del copyright y del mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para obtener más información, escriba la opción de la línea de comandos **\/?** y vea la opción **\/nologo**.|  
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio de registro de seguimiento.|  
|**UndefinePreprocessorDefinitions**|Anular la definición de un símbolo del preprocesador.<br /><br /> Para obtener más información, vea la opción **\/u** en [Utilizar RC \(la línea de comandos de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) en el sitio web de MSDN.  También vea **PreprocessorDefinitions** en esta tabla.|  
  
## Comentarios  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)