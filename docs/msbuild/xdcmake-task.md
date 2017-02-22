---
title: "XDCMake (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), XDCMake (tarea)"
  - "XDCMake (tarea) (MSBuild (Visual C++))"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XDCMake (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Incluye la herramienta Documentación XML \(xdcmake.exe\), que combina archivos de comentarios de documento XML \(.xdc\) en un archivo .xml.  
  
 Se crea un archivo .xdc al proporcionar los comentarios de la documentación en su código fuente de Visual C\+\+ y compilar utilizando la opción de compilador [\/doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp).  Para obtener más información, vea [XDCMake \(Referencia\)](/visual-cpp/ide/xdcmake-reference), [Herramienta Generador de documentos XML \(Páginas de propiedades\)](/visual-cpp/ide/xml-document-generator-tool-property-pages) y la opción de la Ayuda de la línea de comandos \(**\/?**\) de xdcmake.exe.  
  
## Comentarios  
 De forma predeterminada, la herramienta xdcmake.exe admite algunas opciones de la línea de comandos.  Se admiten opciones adicionales al especificar la opción de la línea de comandos **\/old**.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **XDCMake**.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Parámetro **String\[\]** opcional.<br /><br /> Especifica uno o más archivos .xdc adicionales que se desea combinar.<br /><br /> Para obtener más información, vea la descripción de **Archivos de documento adicionales** en [Herramienta Generador de documentos XML \(Páginas de propiedades\)](/visual-cpp/ide/xml-document-generator-tool-property-pages).  También vea las opciones de la línea de comandos **\/old** y **\/Fs** de xdcmake.exe.|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones tal y como se especifica en la línea de comandos.  Por ejemplo, "*\/opción1 \/opción2 \/opción\#*".  Utilice este parámetro para especificar opciones que no son representadas por ningún otro parámetro de tarea **XDCMake**.<br /><br /> Para obtener más información, vea [XDCMake \(Referencia\)](/visual-cpp/ide/xdcmake-reference), [Herramienta Generador de documentos XML \(Páginas de propiedades\)](/visual-cpp/ide/xml-document-generator-tool-property-pages) y la Ayuda de la línea de comandos \(**\/?**\) de xdcmake.exe.|  
|**DocumentLibraryDependencies**|Parámetro **Boolean** opcional.<br /><br /> Si es `true` y el proyecto actual tiene una dependencia en un proyecto de biblioteca estática \(.lib\) en la solución, los archivos .xdc de ese proyecto de biblioteca se incluyen en la salida del archivo .xml del proyecto actual.<br /><br /> Para obtener más información, vea la descripción de **Dependencias de biblioteca de documentos** en [Herramienta Generador de documentos XML \(Páginas de propiedades\)](/visual-cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Reemplaza el nombre de archivo de salida predeterminado.  El nombre predeterminado deriva del nombre del primer archivo .xdc que se procesa.<br /><br /> Para obtener más información, vea la opción **\/out:** `filename` de [XDCMake \(Referencia\)](/visual-cpp/ide/xdcmake-reference).  También vea las opciones de la línea de comandos **\/old** y **\/Fo** de xdcmake.exe.|  
|**ProjectName**|Parámetro **String** opcional.<br /><br /> El nombre del proyecto actual.|  
|**SlashOld**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, habilita opciones de xdcmake.exe adicionales.<br /><br /> Para obtener más información, vea la opción de línea de comandos **\/old** de xdcmake.exe.|  
|**Sources**|Parámetro `ITaskItem[]` requerido.<br /><br /> Define una matriz de elementos de archivo de origen de MSBuild que las tareas pueden usar y emitir.|  
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita la presentación del copyright y del mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para obtener más información, vea la opción **\/nologo** de [XDCMake \(Referencia\)](/visual-cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio del registro de seguimiento.|  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)