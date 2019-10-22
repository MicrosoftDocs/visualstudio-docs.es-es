---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561639"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Si el motor de Windows Script permite que los scriptlets de código de texto sin formato se agreguen al script o permite que el texto de la expresión se evalúe en tiempo de ejecución, implementa la interfaz `IActiveScriptParse`. En el caso de los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo (distinto de `IPersist*`) para obtener el código de script en el motor de scripting y para adjuntar fragmentos de script a varios eventos de objeto. .  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializa el motor de scripting.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Agrega un Scriptlet de código al script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analiza el Scriptlet de código dado, agregando declaraciones en el espacio de nombres y evaluando el código según corresponda.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)