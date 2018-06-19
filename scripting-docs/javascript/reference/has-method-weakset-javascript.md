---
title: Método has (WeakSet) (JavaScript) | Documentos de Microsoft
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dbc7e17e3fd73730386293c5e3f894455e41a93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637015"
---
# <a name="has-method-weakset-javascript"></a>Método has (WeakSet) (JavaScript)
Devuelve `true` si `WeakSet` contiene el elemento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
setObj.has(obj)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `setObj`  
 Obligatorio. Objeto `WeakSet`.  
  
 `obj`  
 Obligatorio. Elemento que se va a comprobar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 `true` si el conjunto contiene el elemento especificado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un `WeakSet` y, a continuación, comprobar si el conjunto contiene un miembro específico.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]