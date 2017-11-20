---
title: "con la instrucción (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>with (Instrucción de JavaScript)
Establece el objeto predeterminado para una instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parámetros  
 `object`  
 Objeto predeterminado.  
  
 `statements`  
 Una o más instrucciones para las que `object` es el objeto predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 La instrucción `with` se utiliza habitualmente para reducir el volumen de código que se ha de escribir en determinadas circunstancias.  
  
> [!WARNING]
>  No se permite el uso de `with` en modo strict. El uso de `with` puede hacer que el código sea más difícil de leer y de depurar y debe evitarse por regla general.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se utiliza el objeto `Math` varias veces:  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>Ejemplo  
 Si vuelve a escribir el ejemplo para usar la instrucción `with`, el código se vuelve más conciso:  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [this (Instrucción)](../../javascript/reference/this-statement-javascript.md)