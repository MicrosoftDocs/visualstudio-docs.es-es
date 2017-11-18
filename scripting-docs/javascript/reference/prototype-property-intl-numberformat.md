---
title: prototype (propiedad, Intl.NumberFormat) | Documentos de Microsoft
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b037ce7476574252966e17fcf64246beeaaea1e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlnumberformat"></a>prototype (Propiedad, Intl.NumberFormat)
Devuelve una referencia al prototipo para un formateador.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
numberFormat.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `numberFormat` argumento es el nombre de un formateador.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `Intl.NumberFormat` que devuelva el valor del elemento más grande del conjunto, declare la función, agréguela a `Intl.NumberFormat.prototype` y, a continuación, úsela.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]