---
title: IActiveScriptParseProcedureOld (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld (Interfaz)
Permite que el texto del código fuente para procedimientos va a agregar a la secuencia de comandos. Para los lenguajes de secuencias de comandos interpretados que no tiene un entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IActiveScriptParse` o `IPersist*`) para agregar los procedimientos de script para el espacio de nombres.  
  
> [!NOTE]
>  Esta interfaz está en desuso en favor de la `IActiveScriptParseProcedure` interfaz.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptParseProcedureOld` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analiza el procedimiento de código especificada y agrega el procedimiento para el espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)