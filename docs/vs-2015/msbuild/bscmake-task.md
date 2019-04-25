---
title: Tarea BscMake | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05290bed3fe51c69e29d8bafef927c91c63b5249
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667266"
---
# <a name="bscmake-task"></a>BscMake (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IMPORTANTE]
>  El IDE de Visual Studio ya no utiliza bscmake. Desde Visual Studio Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf en la carpeta de soluciones.  
  
 Ajusta la herramienta Utilidad de mantenimiento de información de examen de Microsoft (bscmake.exe).  La herramienta bscmake.exe genera un archivo de información de examen (.bsc) a partir de archivos de explorador de origen (.sbr) que se crean durante la compilación. Use el **Examinador de objetos** para ver un archivo .bsc. Para más información, vea [Referencia de BSCMAKE](http://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **BscMake**. La mayoría de los parámetros de tarea corresponden a una opción de línea de comandos.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones especificada en la línea de comando. Por ejemplo, "/*option1* /*option2* /*option#*". Use este parámetro para especificar opciones que no están representadas por ningún otro parámetro de tarea **BscMake**.<br /><br /> Para más información, vea las opciones en [Opciones de BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Especifica un nombre de archivo que invalida el nombre de archivo de salida predeterminado.<br /><br /> Para más información, vea la opción **/o** en [Opciones de BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, fuerza una compilación no incremental. Una compilación no incremental completa tiene lugar independientemente de si existe o no un archivo .bsc, y evita que se trunquen los archivos .sbr.<br /><br /> Para más información, vea la opción **/n** en [Opciones de BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Sources**|Parámetro opcional de tipo **ITaskItem[]**.<br /><br /> Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.|  
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia. <br /><br /> Para más información, vea la opción **/NOLOGO** en [Opciones de BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio de registro de seguimiento.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
