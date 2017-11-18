---
title: constructor (propiedad, Set) | Documentos de Microsoft
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea9af6d60c2ae8bc8a383c4cebbf0955e183895e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-set"></a>constructor (Propiedad, Set)
Especifica la función que crea un conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
set.constructor  
```  
  
## <a name="remarks"></a>Comentarios  
 El `set` requerido es el nombre del conjunto.  
  
 La propiedad `constructor` es un miembro del prototipo de cada objeto que tiene un prototipo. Esto incluye todos los objetos intrínsecos de JavaScript, salvo los objetos `Global` y `Math`. La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]