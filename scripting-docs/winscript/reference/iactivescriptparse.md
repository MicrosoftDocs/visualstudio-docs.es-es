---
title: IActiveScriptParse | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Si la secuencia de comandos de Windows motor permite scriptlets de código de texto sin formato para agregarse a la secuencia de comandos o texto de la expresión se evalúe en tiempo de ejecución, implementa el `IActiveScriptParse` interfaz. Para los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IPersist*`) para obtener el código de script en el motor de scripting y asociar fragmentos de script para varios objetos eventos.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializa el motor de scripting.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Agrega un Subscript de código a la secuencia de comandos.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analiza el scriptlet de código determinado, agregar declaraciones en el espacio de nombres y evaluar el código según corresponda.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)