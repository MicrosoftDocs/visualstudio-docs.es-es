---
title: Función String.fromCodePoint (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0905b392606bec9fb59b08a04129ce30cb013db1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639265"
---
# <a name="stringfromcodepoint-function-javascript"></a>Función String.fromCodePoint (JavaScript)
Devuelve la cadena asociada a un punto de código Unicode UTF-16.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `...codePoints`  
 Obligatorio. Un parámetro de rest que especifica uno o varios valores de punto de código UTF-16.  
  
## <a name="remarks"></a>Comentarios  
 Esta función genera una excepción `RangeError` si `...codePoints` no es un punto de código UTF-16 válido.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo usar la función `fromCodePoint`.  
  
```JavaScript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]