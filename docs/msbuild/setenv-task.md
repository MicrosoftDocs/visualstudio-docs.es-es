---
title: SetEnv (tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea SetEnv para establecer o eliminar el valor de una variable de entorno especificada.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
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
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76fc0d0dafac542ffde8656c643ec01b7ce23a39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861678"
---
# <a name="setenv-task"></a>Tarea SetEnv

Establece o elimina el valor de una variable de entorno especificada.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla, se describen los parámetros de la tarea **SetEnv**.

|Parámetro|Descripción|
|---------------|-----------------|
|**Nombre**|Parámetro obligatorio de tipo **String**.<br /><br /> Nombre de una variable de entorno.|
|**OutputEnvironmentVariable**|Parámetro de salida de tipo **String** opcional.<br /><br /> Contiene el valor que se asigna a la variable de entorno especificada por el parámetro **Name**.|
|**Prefijo**|Parámetro `Boolean` obligatorio.<br /><br /> Si es `true`, concatena el valor del parámetro **Value** antes del valor de la variable de entorno especificada por el parámetro **Name** y, después, asigna el resultado a la variable de entorno. Si es `false`, solo asigna el valor del parámetro **Value** a la variable de entorno.|
|**Destino**|Parámetro **String** opcional.<br /><br /> Especifica la ubicación en que se almacena una variable de entorno. Especifique "User" o "Machine".<br /><br /> Para obtener más información, vea [EnvironmentVariableTarget Enum](xref:System.EnvironmentVariableTarget).|
|**Valor**|Parámetro **String** opcional.<br /><br /> Valor asignado a la variable de entorno especificada por el parámetro **Name**. Si **Value** está vacío y la variable existe, se elimina la variable. Si la variable no existe, no se produce ningún error, aunque no se puede realizar la operación.<br /><br /> Para obtener más información, vea [Environment::SetEnvironmentVariable Method](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
