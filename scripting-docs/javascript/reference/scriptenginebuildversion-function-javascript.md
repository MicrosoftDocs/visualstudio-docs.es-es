---
title: "ScriptEngineBuildVersion (función de JavaScript) | Documentos de Microsoft"
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
- ScriptEngineBuildVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineBuildVersion function
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd458d43bebfb0d0e0b2cb6bebb483c22a60b4f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginebuildversion-function-javascript"></a>ScriptEngineBuildVersion (Función de JavaScript)
Obtiene el número de versión de compilación del motor de scripting en uso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ScriptEngineBuildVersion()  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto corresponde directamente a la información de versión contenida en la biblioteca de vínculos dinámicos (DLL) para el lenguaje de scripting en uso.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `ScriptEngineBuildVersion`:  
  
```JavaScript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ScriptEngine (función)](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineMajorVersion (función)](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion (Función)](../../javascript/reference/scriptengineminorversion-function-javascript.md)