---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8325ffcb21f1871ca742611e6587df02ef3b89c8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349015"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Si la secuencia de comandos de Windows permite scriptlets de código de texto sin formato que se agregarán a la secuencia de comandos motor o texto de la expresión se evalúe en tiempo de ejecución, implementa el `IActiveScriptParse` interfaz. Para los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IPersist*`) para obtener el código de script en el motor de scripting y adjuntar fragmentos de secuencias de comandos a varios objetos eventos.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializa el motor de scripting.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Agrega un scriptlet de código a la secuencia de comandos.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analiza el scriptlet de código dado, agregando declaraciones en el espacio de nombres y evaluando código según corresponda.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)