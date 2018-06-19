---
title: tiene (método, Set) (JavaScript) | Documentos de Microsoft
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636725"
---
# <a name="has-method-set-javascript"></a>has (Método, Set de JavaScript)
Devuelve `true` si el conjunto contiene el elemento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `setObj`  
 Obligatorio. Objeto `Set`.  
  
 `value`  
 Obligatorio. Elemento que se va a comprobar.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 `true` si el conjunto contiene el elemento especificado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un `Set` y, a continuación, comprobar si el conjunto contiene un miembro específico.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]