---
title: Interfaz Iactivescriptparseprocedureold (| Microsoft Docs
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
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571426"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld (Interfaz)
Permite agregar el texto de código fuente para los procedimientos al script. En el caso de los lenguajes de scripting interpretados que no tienen un entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo (distinto de `IActiveScriptParse` o `IPersist*`) para agregar procedimientos de script al espacio de nombres.  
  
> [!NOTE]
> Esta interfaz está en desuso en favor de la interfaz `IActiveScriptParseProcedure`.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, la interfaz de `IActiveScriptParseProcedureOld` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analiza el procedimiento de código dado y agrega el procedimiento al espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)