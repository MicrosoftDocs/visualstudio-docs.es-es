---
title: prototype (propiedad) (WeakSet) | Documentos de Microsoft
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c66c7854a83dcf3128025350a7fcdd17f4dfaf5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakset"></a>Propiedad prototype (WeakSet)
Devuelve una referencia al prototipo para una `WeakSet`.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
weakset.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento de `weakset` es el nombre de un conjunto.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `WeakSet` que devuelva el valor del elemento más grande del conjunto, declare la función, agréguela a `WeakSet.prototype` y, a continuación, úsela.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]