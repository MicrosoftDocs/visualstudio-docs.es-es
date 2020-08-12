---
title: IActiveScriptParseProcedure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3567a22eac2ad270739e62e0f0fb9914bdf4a9ec
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144576"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Si el motor de Windows Script permite agregar el texto de código fuente para los procedimientos al script, implementa la `IActiveScriptParseProcedure` interfaz. En el caso de los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo (distinto de `IActiveScriptParse` o `IPersist` *) para agregar procedimientos de script al espacio de nombres.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|
|-|-|
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analiza el procedimiento de código dado y agrega el procedimiento al espacio de nombres.|  
  
## <a name="see-also"></a>Consulte también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)