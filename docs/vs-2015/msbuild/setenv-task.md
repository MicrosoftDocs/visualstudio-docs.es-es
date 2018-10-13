---
title: Tarea SetEnv | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 0c15f0be4498c3ff3014c273d31657851c9e65b8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205678"
---
# <a name="setenv-task"></a>SetEnv (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Establece o elimina el valor de una variable de entorno especificada.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla, se describen los parámetros de la tarea **SetEnv**.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**Name**|Parámetro obligatorio de tipo **String**.<br /><br /> Nombre de una variable de entorno.|  
|**OutputEnvironmentVariable**|Parámetro de salida de tipo **String** opcional.<br /><br /> Contiene el valor que se asigna a la variable de entorno especificada por el parámetro **Name**.|  
|**Prefix**|Parámetro `Boolean` obligatorio.<br /><br /> Si es `true`, concatena el valor del parámetro **Value** antes del valor de la variable de entorno especificada por el parámetro **Name** y, después, asigna el resultado a la variable de entorno. Si es `false`, solo asigna el valor del parámetro **Value** a la variable de entorno.|  
|**Target**|Parámetro **String** opcional.<br /><br /> Especifica la ubicación en que se almacena una variable de entorno. Especifique “`User`” o “`Machine`”.<br /><br /> Para obtener más información, vea "Enumeración EnvironmentVariableTarget" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Valor**|Parámetro **String** opcional.<br /><br /> Valor asignado a la variable de entorno especificada por el parámetro **Name**. Si **Value** está vacío y la variable existe, se elimina la variable. Si la variable no existe, no se produce ningún error, aunque no se puede realizar la operación.<br /><br /> Para más información, vea "Método Environment::SetEnvironmentVariable" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



