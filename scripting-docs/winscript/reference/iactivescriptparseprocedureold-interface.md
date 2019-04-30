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
ms.openlocfilehash: 520d3f1414447abfc7c018d36853b72aefbbf15f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386172"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld (Interfaz)
Permite que el texto del código fuente para los procedimientos que se agregarán a la secuencia de comandos. Para los lenguajes de scripting interpretados que no tienen un entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IActiveScriptParse` o `IPersist*`) para agregar los procedimientos de la secuencia de comandos para el espacio de nombres.  
  
> [!NOTE]
> Esta interfaz está en desuso en favor de la `IActiveScriptParseProcedure` interfaz.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptParseProcedureOld` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analiza el procedimiento de código especificado y agrega el procedimiento para el espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)