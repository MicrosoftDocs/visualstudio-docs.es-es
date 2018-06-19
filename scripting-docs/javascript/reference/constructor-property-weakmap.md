---
title: constructor (propiedad, WeakMap) | Documentos de Microsoft
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
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c7340e1e5eeff9a80e231cf1aa49443adc94e72
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636045"
---
# <a name="constructor-property-weakmap"></a>constructor (Propiedad, WeakMap)
Especifica la función que crea un `WeakMap` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
weakmap.constructor  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `weakmap` es el nombre de la `WeakMap` objeto.  
  
 La propiedad `constructor` es un miembro del prototipo de cada objeto que tiene un prototipo. Esto incluye todos los objetos intrínsecos de JavaScript, salvo los objetos `Global` y `Math`. La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]