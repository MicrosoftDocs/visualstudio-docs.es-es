---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71a22f422ff04e56a7aaa7a715641d190ade47bf
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144394"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Si el motor de Windows Script permite agregar el texto de código fuente para los procedimientos al script, implementa la `IActiveScriptParseProcedure32` interfaz. En el caso de los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo (distinto de `IActiveScriptParse32` o `IPersist` *) para agregar procedimientos de script al espacio de nombres.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|
|-|-|
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analiza el procedimiento de código dado y agrega el procedimiento al espacio de nombres.|  
  
## <a name="see-also"></a>Consulte también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)