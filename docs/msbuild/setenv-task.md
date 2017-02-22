---
title: "SetEnv (Tarea) | Microsoft Docs"
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
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tareas"
  - "SetEnv (tarea) (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SetEnv (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Establece o elimina el valor de una variable de entorno especificada.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **SetEnv** .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**Name**|Parámetro **String** requerido.<br /><br /> Nombre de una variable de entorno.|  
|**OutputEnvironmentVariable**|Parámetro de salida **String** opcional.<br /><br /> Contiene el valor que se asigna a la variable de entorno que especifica el parámetro **Name**.|  
|**Prefix**|Parámetro `Boolean` obligatorio.<br /><br /> Si es `true`, concatena el valor del parámetro **Value** antes del valor de la variable de entorno que es especificada por el parámetro **Name** y, a continuación, asigna el resultado a la variable de entorno.  Si es `false`, solo asigna el valor del parámetro **Value** a la variable de entorno.|  
|**Target**|Parámetro **String** opcional.<br /><br /> Especifica la ubicación donde se almacena una variable de entorno.  Especifique "`Usuario`" o "`Máquina`".<br /><br /> Para obtener más información, vea "EnvironmentVariableTarget Enumeration" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Value**|Parámetro **String** opcional.<br /><br /> El valor asignado a la variable de entorno especificado por el parámetro **Name**.  Si **Value** está vacío y la variable existe, se elimina la variable.  Si no existe la variable, no se produce ningún error aunque no se pueda realizar la operación.<br /><br /> Para obtener más información, vea "Environment::SetEnvironmentVariable Method" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## Comentarios  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)