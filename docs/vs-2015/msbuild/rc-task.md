---
title: RC (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9bc8b770e654442f14e693fda35d7cf6f5edbd12
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654834"
---
# <a name="rc-task"></a>RC (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Incluye la herramienta Compilador de recursos de Microsoft Windows (rc.exe). La tarea **RC** compila recursos, como cursores, iconos, mapas de bits, cuadros de diálogo y fuentes, en un archivo de recursos (.res). Para obtener más información, vea "Resource Compiler" (Compilador de recursos) en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea RC. La mayoría de los parámetros de tarea, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parámetro **String[]** opcional.<br /><br /> Agrega un directorio a la lista de directorios en que se buscan archivos de inclusión.<br /><br /> Para obtener más información, vea la opción **/I** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN.|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones de línea de comandos de ejemplo, **"**_/option1 /option2 /option#_". Use este parámetro para especificar opciones de la línea de comandos que no están representadas por ningún otro parámetro de tarea **RC**.<br /><br /> Para obtener más información, vea las opciones de [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN.|  
|**Referencia cultural**|Parámetro **String** opcional.<br /><br /> Especifica un identificador de configuración regional que representa la referencia cultural usada en los recursos.<br /><br /> Para obtener más información, vea la opción **/l** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN.|  
|**IgnoreStandardIncludePath**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, impide que el compilador de recursos compruebe la variable de entorno INCLUDE cuando busca archivos de encabezado o archivos de recursos.<br /><br /> Para obtener más información, vea la opción **/x** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN.|  
|**NullTerminateStrings**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, se finalizan todas las cadenas de la tabla de strings con NULL.<br /><br /> Para obtener más información, vea la opción **/n** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN.|  
|**PreprocessorDefinitions**|Parámetro **String[]** opcional.<br /><br /> Defina uno o varios símbolos de preprocesador para el compilador de recursos. Especifique una lista de símbolos de macro.<br /><br /> Para obtener más información, vea la opción **/d** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN. Vea también **UndefinePreprocessorDefinitions** en esta tabla.|  
|**ResourceOutputFileName**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de recursos. Especifique un nombre de archivo de recursos.<br /><br /> Para obtener más información, vea la opción **/fo** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN.|  
|**ShowProgress**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, muestra mensajes que informan del progreso del compilador.<br /><br /> Para obtener más información, vea la opción **/v** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN.|  
|**Origen**|Parámetro `ITaskItem[]` requerido.<br /><br /> Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.|  
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia. <br /><br /> Para obtener más información, escriba la opción de línea de comandos **/?** y consulte la opción **/nologo**.|  
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio del registro de seguimiento.|  
|**UndefinePreprocessorDefinitions**|Anula la definición de un símbolo de preprocesador.<br /><br /> Para obtener más información, vea la opción **/u** en [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Usar RC [línea de comandos de RC]) en el sitio web de MSDN. Vea también **PreprocessorDefinitions** en esta tabla.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
