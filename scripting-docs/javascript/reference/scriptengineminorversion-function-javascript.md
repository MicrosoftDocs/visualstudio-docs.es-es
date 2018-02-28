---
title: "ScriptEngineMinorVersion (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengineminorversion-function-javascript"></a>ScriptEngineMinorVersion (Función de JavaScript)
Obtiene el número de versión secundaria del motor de scripting en uso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto corresponde directamente a la información de versión contenida en la biblioteca de vínculos dinámicos (DLL) para el lenguaje de scripting en uso.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngineMinorVersion`.  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ScriptEngine (función)](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion (función)](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion (Función)](../../javascript/reference/scriptenginemajorversion-function-javascript.md)