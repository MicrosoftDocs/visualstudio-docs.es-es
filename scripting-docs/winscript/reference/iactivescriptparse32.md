---
title: IActiveScriptParse32 | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724405"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Si la secuencia de comandos de Windows motor permite scriptlets de código de texto sin formato para agregarse a la secuencia de comandos o texto de la expresión se evalúe en tiempo de ejecución, implementa el `IActiveScriptParse32` interfaz. Para los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IPersist*`) para obtener el código de script en el motor de scripting y asociar fragmentos de script para varios objetos eventos.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Agrega un Subscript de código a la secuencia de comandos.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inicializa el motor de scripting.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analiza el scriptlet de código determinado, agregar declaraciones en el espacio de nombres y evaluar el código según corresponda.|