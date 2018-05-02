---
title: IActiveScriptParseProcedure32 | Documentos de Microsoft
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
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Si el motor de scripts de Windows permite que el texto del código fuente para procedimientos va a agregar a la secuencia de comandos, que implementa el `IActiveScriptParseProcedure32` interfaz. Para los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IActiveScriptParse32` o `IPersist`*) para agregar los procedimientos de script al espacio de nombres.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analiza el procedimiento de código especificada y agrega el procedimiento para el espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)