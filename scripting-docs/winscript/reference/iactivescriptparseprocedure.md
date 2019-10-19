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
ms.openlocfilehash: c20947a125766547565d99c5762c20e23652da1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561673"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Si el motor de Windows Script permite agregar el texto de código fuente para los procedimientos al script, implementa la interfaz `IActiveScriptParseProcedure`. En el caso de los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo (distinto de `IActiveScriptParse` o `IPersist` *) para agregar procedimientos de script al espacio de nombres.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analiza el procedimiento de código dado y agrega el procedimiento al espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)