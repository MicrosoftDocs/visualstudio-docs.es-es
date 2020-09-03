---
title: Tarea SetEnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 960ebb94cf03ef293011645e732a0f0379d0fd47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852246"
---
# <a name="setenv-task"></a>SetEnv (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Establece o elimina el valor de una variable de entorno especificada.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla, se describen los parámetros de la tarea **SetEnv**.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|**Name**|Parámetro obligatorio de tipo **String**.<br /><br /> Nombre de una variable de entorno.|  
|**OutputEnvironmentVariable**|Parámetro de salida de tipo **String** opcional.<br /><br /> Contiene el valor que se asigna a la variable de entorno especificada por el parámetro **Name**.|  
|**Prefix**|Parámetro `Boolean` obligatorio.<br /><br /> Si es `true`, concatena el valor del parámetro **Value** antes del valor de la variable de entorno especificada por el parámetro **Name** y, después, asigna el resultado a la variable de entorno. Si es `false`, solo asigna el valor del parámetro **Value** a la variable de entorno.|  
|**Target**|Parámetro **String** opcional.<br /><br /> Especifica la ubicación en que se almacena una variable de entorno. Especifique “`User`” o “`Machine`”.<br /><br /> Para obtener más información, vea "Enumeración EnvironmentVariableTarget" en el sitio web de [MSDN](https://msdn.microsoft.com/).|  
|**Valor**|Parámetro **String** opcional.<br /><br /> Valor asignado a la variable de entorno especificada por el parámetro **Name**. Si **Value** está vacío y la variable existe, se elimina la variable. Si la variable no existe, no se produce ningún error, aunque no se puede realizar la operación.<br /><br /> Para más información, vea "Método Environment::SetEnvironmentVariable" en el sitio web de [MSDN](https://msdn.microsoft.com/).|  
  
## <a name="remarks"></a>Observaciones  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
