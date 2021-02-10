---
title: Tarea XDCMake | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea XDCMake para encapsular la herramienta de documentación XML xdcmake.exe, que combina archivos de comentario de documentación XML en un archivo .xml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a867146d48b5ba6c4bfb2ac33b45c505b6f6c37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971055"
---
# <a name="xdcmake-task"></a>XDCMake (tarea)

Incluye la herramienta Documentación XML (*xdcmake.exe*), que combina archivos de comentarios de documento XML ( *.xdc*) en un archivo *.xml*.

 Se crea un archivo *.xdc* cuando proporciona comentarios de documentación en el código fuente de C++ y compila mediante la opción del compilador [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Para más información, consulte [Referencia de XDCMake](/cpp/build/reference/xdcmake-reference), [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/build/reference/xml-document-generator-tool-property-pages) y la opción de ayuda de la línea de comandos ( **/?** ) de *xdcmake.exe*.

## <a name="remarks"></a>Observaciones

 De forma predeterminada, la herramienta *xdcmake.exe* admite algunas opciones de la línea de comandos. Se admiten opciones adicionales al especificar la opción de la línea de comandos **/old**.

## <a name="parameters"></a>Parámetros

 En la tabla siguiente se describen los parámetros de la tarea **XDCMake**.

|Parámetro|Description|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parámetro **String[]** opcional.<br /><br /> Especifica uno o más archivos *.xdc* adicionales que se van a combinar.<br /><br /> Para más información, consulte la descripción **Archivos de documento adicionales** en [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Consulte también las opciones de la línea de comandos **/old** y **/Fs** de *xdcmake.exe*.|
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones especificada en la línea de comando. Por ejemplo, /\<option1> /\<option2> /\<option#>. Use este parámetro para especificar opciones que no están representadas por ningún otro parámetro de tarea **XDCMake**.<br /><br /> Para más información, consulte [Referencia de XDCMake](/cpp/build/reference/xdcmake-reference), [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/build/reference/xml-document-generator-tool-property-pages) y la ayuda de la línea de comandos ( **/?** ) de *xdcmake.exe*.|
|**DocumentLibraryDependencies**|Parámetro **Boolean** opcional.<br /><br /> Si es `true` y el proyecto actual tiene una dependencia en un proyecto de biblioteca estática ( *.lib*) en la solución, los archivos *.xdc* de ese proyecto de biblioteca se incluyen en la salida del archivo *.xml* para el proyecto actual.<br /><br /> Para más información, consulte la descripción **Dependencias de biblioteca de documentos** en [Páginas de propiedades de la herramienta Generador de documentos XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Reemplaza el nombre del archivo de salida predeterminado. El nombre predeterminado se deriva del nombre del primer archivo *.xdc* procesado.<br /><br /> Para obtener más información, vea la opción **/out:\<filename>** en [Referencia de XDCMake](/cpp/build/reference/xdcmake-reference). Consulte también las opciones de la línea de comandos **/old** y **/Fo** de *xdcmake.exe*.|
|**ProjectName**|Parámetro **String** opcional.<br /><br /> Nombre del proyecto actual.|
|**SlashOld**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, habilita opciones adicionales de *xdcmake.exe*.<br /><br /> Para más información, consulte la opción de línea de comandos **/old** de *xdcmake.exe*.|
|**Sources**|Parámetro `ITaskItem[]` requerido.<br /><br /> Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.|
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para más información, consulte la opción **/nologo** de [Referencia de XDCMake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio de registro de seguimiento.|

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)