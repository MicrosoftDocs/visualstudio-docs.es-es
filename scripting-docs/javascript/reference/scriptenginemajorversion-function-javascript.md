---
title: "ScriptEngineMajorVersion (función de JavaScript) | Documentos de Microsoft"
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
- ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginemajorversion-function-javascript"></a>ScriptEngineMajorVersion (Función de JavaScript)
Obtiene el número de versión principal del motor de scripting en uso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto corresponde directamente a la información de versión contenida en la biblioteca de vínculos dinámicos (DLL) para el lenguaje de scripting en uso.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngineMajorVersion`:  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ScriptEngine (función)](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion (función)](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion (Función)](../../javascript/reference/scriptengineminorversion-function-javascript.md)