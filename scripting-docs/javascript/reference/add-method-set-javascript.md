---
title: Add (método) (Set) (JavaScript) | Documentos de Microsoft
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633175"
---
# <a name="add-method-set-javascript"></a>add (Método, Set de JavaScript)
Agrega un nuevo elemento a un conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `setObj`  
 Obligatorio. Objeto `Set`.  
  
 `value`  
 Obligatorio. Nuevo elemento del objeto `Set`.  
  
## <a name="remarks"></a>Comentarios  
 El nuevo elemento puede ser de cualquier tipo y debe ser único. Si agrega un elemento que no es único a `Set`, el nuevo elemento no se agregará a la colección.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a set y después recuperarlos.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]