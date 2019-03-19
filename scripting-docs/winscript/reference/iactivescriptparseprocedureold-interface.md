---
title: IActiveScriptParseProcedureOld (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99fa06086bfad56b266b043716e82181aa4c97d5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160633"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld (Interfaz)
Permite que el texto del código fuente para los procedimientos que se agregarán a la secuencia de comandos. Para los lenguajes de scripting interpretados que no tienen un entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IActiveScriptParse` o `IPersist*`) para agregar los procedimientos de la secuencia de comandos para el espacio de nombres.  
  
> [!NOTE]
>  Esta interfaz está en desuso en favor de la `IActiveScriptParseProcedure` interfaz.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptParseProcedureOld` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analiza el procedimiento de código especificado y agrega el procedimiento para el espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)