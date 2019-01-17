---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 10cdff328216d06a3326dd3595ef8fc78bc9cfc9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348118"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Si el motor de scripts de Windows permite que el texto del código fuente para los procedimientos que se agregarán a la secuencia de comandos, implementa el `IActiveScriptParseProcedure32` interfaz. Para los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IActiveScriptParse32` o `IPersist`*) para agregar los procedimientos de script al espacio de nombres.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analiza el procedimiento de código especificado y agrega el procedimiento al espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)