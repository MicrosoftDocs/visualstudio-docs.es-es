---
title: Tarea XDCMake | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c16c92b41aa0635ecb24d83e30e2c347620b2c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675536"
---
# <a name="xdcmake-task"></a>XDCMake (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Incluye la herramienta Documentación XML (xdcmake.exe), que combina archivos de comentarios de documento XML (.xdc) en un archivo .xml.  
  
 Se crea un archivo .xdc cuando proporciona comentarios de documentación en el código fuente de Visual C++ y compila mediante la opción del compilador [/doc](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Para obtener más información, vea [referencia de xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), páginas de propiedades de la [herramienta Generador de documentos XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)y la opción de ayuda de la línea de comandos (**/?**) para obtener xdcmake.exe.  
  
## <a name="remarks"></a>Observaciones  
 De forma predeterminada, la herramienta xdcmake.exe admite algunas opciones de la línea de comandos. Se admiten opciones adicionales al especificar la opción de la línea de comandos **/old**.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea **XDCMake**.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Parámetro **String[]** opcional.<br /><br /> Especifica uno o más archivos .xdc adicionales que se van a combinar.<br /><br /> Para obtener más información, vea la descripción de **los archivos de documento adicionales** en páginas de propiedades de la [herramienta Generador de documentos XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Vea también las opciones de línea de comandos **/Old** y **/FS** para xdcmake.exe.|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones especificada en la línea de comando. Por ejemplo, "*/opción1 /opción2 /opción#*". Use este parámetro para especificar opciones que no están representadas por ningún otro parámetro de tarea **XDCMake**.<br /><br /> Para obtener más información, vea [referencia de xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), páginas de propiedades de la [herramienta Generador de documentos XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)y ayuda de la línea de comandos (**/?**) para obtener xdcmake.exe.|  
|**DocumentLibraryDependencies**|Parámetro **Boolean** opcional.<br /><br /> Si es `true` y el proyecto actual tiene una dependencia en un proyecto de biblioteca estática (.lib) en la solución, los archivos .xdc de ese proyecto de biblioteca se incluyen en la salida del archivo .xml para el proyecto actual.<br /><br /> Para obtener más información, vea la descripción de las **dependencias** de la biblioteca de documentos en páginas de propiedades de la [herramienta Generador de documentos XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Reemplaza el nombre del archivo de salida predeterminado. El nombre predeterminado se deriva del nombre del primer archivo .xdc procesado.<br /><br /> Para obtener más información, vea la opción **/out:** `filename` en [referencia de xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Vea también las opciones de línea de comandos **/Old** y **/fo** para obtener xdcmake.exe.|  
|**ProjectName**|Parámetro **String** opcional.<br /><br /> Nombre del proyecto actual.|  
|**SlashOld**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, habilita opciones adicionales de xdcmake.exe.<br /><br /> Para obtener más información, consulte la opción de línea de comandos **/Old** para obtener xdcmake.exe.|  
|**Sources**|Parámetro `ITaskItem[]` requerido.<br /><br /> Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.|  
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para más información, vea la opción **/nologo:** en [Referencia de XDCMake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio de registro de seguimiento.|  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
