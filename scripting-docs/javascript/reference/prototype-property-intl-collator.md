---
title: prototype (propiedad, Intl.Collator) | Documentos de Microsoft
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlcollator"></a>prototype (Propiedad, Intl.Collator)
Devuelve una referencia al prototipo para un clasificador.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `collator` argumento es el nombre de un clasificador.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `Intl.Collator` que devuelva el valor del elemento más grande del conjunto, declare la función, agréguela a `Intl.Collator.prototype` y, a continuación, úsela.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]