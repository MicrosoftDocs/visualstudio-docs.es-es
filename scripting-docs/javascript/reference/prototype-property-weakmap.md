---
title: prototype (propiedad, WeakMap) | Documentos de Microsoft
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639255"
---
# <a name="prototype-property-weakmap"></a>prototype (Propiedad, WeakMap)
Devuelve una referencia al prototipo correspondiente a un `WeakMap` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `weakmap` argumento es el nombre de un `WeakMap` objeto.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método a la `WeakMap` objeto que devuelve el valor del elemento más grande de la `WeakMap`, declare la función, agréguela a `WeakMap.prototype`y, a continuación, usarla.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]