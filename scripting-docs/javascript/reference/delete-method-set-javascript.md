---
title: Delete (método) (Set) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636095"
---
# <a name="delete-method-set-javascript"></a>delete (Método, Set de JavaScript)
Quita el elemento especificado de un conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `setObj`  
 Obligatorio. Objeto `Set`.  
  
 `value`  
 Obligatorio. Elemento que se va a quitar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 `true` si se ha eliminado el elemento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un `Set` y, a continuación, elimine uno de ellos.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]