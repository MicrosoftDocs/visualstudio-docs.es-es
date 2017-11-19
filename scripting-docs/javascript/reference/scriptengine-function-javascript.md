---
title: "ScriptEngine (función de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngine
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngine function
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d441fcce065677f7b673a9979acff9cf9aa2ce90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengine-function-javascript"></a>ScriptEngine (Función de JavaScript)
Obtiene el nombre del lenguaje de scripting en uso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ScriptEngine()  
```  
  
## <a name="remarks"></a>Comentarios  
 La función `ScriptEngine` devuelve "JScript", lo que indica que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es el motor de scripting actual.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngine`:  
  
```JavaScript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ScriptEngineBuildVersion (función)](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion (función)](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion (Función)](../../javascript/reference/scriptengineminorversion-function-javascript.md)