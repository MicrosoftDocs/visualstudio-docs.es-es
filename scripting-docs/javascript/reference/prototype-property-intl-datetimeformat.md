---
title: prototype (propiedad, Intl.DateTimeFormat) | Documentos de Microsoft
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64dff17e4aaf62940f4c9c5f8b422fcbceb7212a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intldatetimeformat"></a>prototype (Propiedad, Intl.DateTimeFormat)
Devuelve una referencia al prototipo para un formateador.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
dateTimeFormat.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `dateTimeFormat` argumento es el nombre de un formateador.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `Intl.DateTimeFormat` que devuelva el valor del elemento más grande del conjunto, declare la función, agréguela a `Intl.DateTimeFormat.prototype` y, a continuación, úsela.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]