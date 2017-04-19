---
title: Tarea XDCMake | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 491786ecc75c3a396098d434e58e4f6635a3844c
ms.lasthandoff: 04/05/2017

---
# <a name="xdcmake-task"></a>XDCMake (Tarea)
Incluye la herramienta Documentación XML (xdcmake.exe), que combina archivos de comentarios de documento XML (.xdc) en un archivo .xml.  
  
 Se crea un archivo .xdc cuando proporciona comentarios de documentación en el código fuente de Visual C++ y compila mediante la opción del compilador [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Para más información, vea [Referencia de XDCMake](/cpp/ide/xdcmake-reference), [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/ide/xml-document-generator-tool-property-pages) y la opción de ayuda de la línea de comandos (**/?**) de xdcmake.exe.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, la herramienta xdcmake.exe admite algunas opciones de la línea de comandos. Se admiten opciones adicionales al especificar la opción de la línea de comandos **/old**.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea **XDCMake**.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Parámetro **String[]** opcional.<br /><br /> Especifica uno o más archivos .xdc adicionales que se van a combinar.<br /><br /> Para más información, vea la descripción **Archivos de documento adicionales** en [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/ide/xml-document-generator-tool-property-pages). Vea también las opciones de la línea de comandos **/old** y **/Fs** de xdcmake.exe.|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones especificada en la línea de comando. Por ejemplo, "*/option1 /option2 /option#*". Use este parámetro para especificar opciones que no están representadas por ningún otro parámetro de tarea **XDCMake**.<br /><br /> Para más información, vea [Referencia de XDCMake](/cpp/ide/xdcmake-reference), [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/ide/xml-document-generator-tool-property-pages) y la ayuda de la línea de comandos (**/?**) de xdcmake.exe.|  
|**DocumentLibraryDependencies**|Parámetro **Boolean** opcional.<br /><br /> Si es `true` y el proyecto actual tiene una dependencia en un proyecto de biblioteca estática (.lib) en la solución, los archivos .xdc de ese proyecto de biblioteca se incluyen en la salida del archivo .xml para el proyecto actual.<br /><br /> Para más información, vea la descripción **Dependencias de biblioteca de documentos** en [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Reemplaza el nombre del archivo de salida predeterminado. El nombre predeterminado se deriva del nombre del primer archivo .xdc procesado.<br /><br /> Para más información, vea la opción **/out:**`filename` en [Referencia de XDCMake](/cpp/ide/xdcmake-reference). Vea también las opciones de la línea de comandos **/old** y **/Fo** de xdcmake.exe.|  
|**ProjectName**|Parámetro **String** opcional.<br /><br /> Nombre del proyecto actual.|  
|**SlashOld**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, habilita opciones adicionales de xdcmake.exe.<br /><br /> Para más información, vea la opción de línea de comandos **/old** de xdcmake.exe.|  
|**Sources**|Parámetro `ITaskItem[]` requerido.<br /><br /> Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.|  
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia. <br /><br /> Para más información, vea la opción **/nologo:** en [Referencia de XDCMake](/cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio de registro de seguimiento.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
