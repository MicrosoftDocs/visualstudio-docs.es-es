---
title: "Método Add (WeakSet) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-weakset-javascript"></a>Método add (WeakSet) (JavaScript)
Agrega un nuevo elemento a un `WeakSet`.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `weaksetObj`  
 Obligatorio. Objeto `WeakSet`.  
  
 `obj`  
 Obligatorio. Nuevo elemento del objeto `WeakSet`.  
  
## <a name="remarks"></a>Comentarios  
 El nuevo elemento debe ser un objeto, y no un valor arbitrario, y además debe ser único. Si agrega un elemento que no es único a `WeakSet`, el nuevo elemento no se agregará a la colección.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo agregar miembros a un conjunto y verificar que se hayan agregado.  
  
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