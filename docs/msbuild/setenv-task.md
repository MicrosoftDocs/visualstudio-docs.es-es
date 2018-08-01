---
title: Tarea SetEnv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2d9cec2c76b2159e14b1e7abe19b93ab91f6688
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153779"
---
# <a name="setenv-task"></a>Tarea SetEnv
Establece o elimina el valor de una variable de entorno especificada.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla, se describen los parámetros de la tarea **SetEnv**.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**Name**|Parámetro obligatorio de tipo **String**.<br /><br /> Nombre de una variable de entorno.|  
|**OutputEnvironmentVariable**|Parámetro de salida de tipo **String** opcional.<br /><br /> Contiene el valor que se asigna a la variable de entorno especificada por el parámetro **Name**.|  
|**Prefix**|Parámetro `Boolean` obligatorio.<br /><br /> Si es `true`, concatena el valor del parámetro **Value** antes del valor de la variable de entorno especificada por el parámetro **Name** y, después, asigna el resultado a la variable de entorno. Si es `false`, solo asigna el valor del parámetro **Value** a la variable de entorno.|  
|**Target**|Parámetro **String** opcional.<br /><br /> Especifica la ubicación en que se almacena una variable de entorno. Especifique "User" o "Machine".<br /><br /> Para más información, consulte [Enumeración de EnvironmentVariableTarget](https://msdn.microsoft.com/library/system.environmentvariabletarget(v=vs.110).aspx) en el sitio web de MSDN.|  
|**Valor**|Parámetro **String** opcional.<br /><br /> Valor asignado a la variable de entorno especificada por el parámetro **Name**. Si **Value** está vacío y la variable existe, se elimina la variable. Si la variable no existe, no se produce ningún error, aunque no se puede realizar la operación.<br /><br /> Para más información, consulte [Método Environment::SetEnvironmentVariable](https://msdn.microsoft.com/library/96xafkes(v=vs.110).aspx) en el sitio web de MSDN.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)