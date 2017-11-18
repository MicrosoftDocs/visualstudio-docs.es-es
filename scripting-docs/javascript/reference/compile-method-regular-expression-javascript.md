---
title: "Compile (método) (expresión Regular) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>compile (Método, Regular Expression de JavaScript)
Compila una expresión regular en un formato interno para una ejecución más rápida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>Parámetros  
 `rgExp`  
 Obligatorio. Una instancia de un **expresión Regular** objeto. Puede ser un nombre de variable o un literal.  
  
 *patrón*  
 Obligatorio. Una expresión de cadena que contiene un patrón de expresión regular se compile  
  
 `flags`  
 Opcional. Los marcadores disponibles, que se pueden combinar, son:  
  
-   g (búsqueda global para todas las apariciones de *patrón*)  
  
-   i (no distinguir mayús./minús.)  
  
-   m (búsqueda de múltiples líneas)  
  
## <a name="remarks"></a>Comentarios  
 El **compilar** método convierte *patrón* en un formato interno para una ejecución más rápida. Esto permite un uso más eficaz de las expresiones regulares en bucles, por ejemplo. Una expresión regular compilada acelera cosas cuando se reutiliza la misma expresión repetidamente. No se obtienen ventajas, sin embargo, si cambia la expresión regular.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **compilar** método:  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)