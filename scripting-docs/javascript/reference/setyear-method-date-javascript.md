---
title: setYear (método, Date) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640285"
---
# <a name="setyear-method-date-javascript"></a>setYear (Método, Date de JavaScript)
Establece el valor de año de la `Date` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>Parámetros  
 `dateObj`  
 Obligatorio. Cualquier objeto `Date`.  
  
 `numYear`  
 Obligatorio. Para los años 1900 y 1999, esto es un valor numérico igual al año menos 1900. Para las fechas fuera de ese intervalo, se trata de un valor numérico de 4 dígitos.  
  
## <a name="remarks"></a>Comentarios  
 Este método está obsoleto y se mantiene la compatibilidad con versiones anteriores. Use el método `setFullYear` en su lugar.  
  
 Para establecer el año de un `Date` objeto 1997, llamada **setYear(97)**. Para establecer el año en 2010, llame a **setYear(2010)**. Por último, para establecer el año en un año en el intervalo de 0 y 99, utilice el `setFullYear` método.  
  
> [!NOTE]
>  Para [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] versión 1.0, `setYear` utiliza un valor que es el resultado de la adición de 1900 y el valor del año proporcionado por `numYear`, independientemente del valor del año. Por ejemplo, para establecer el año 1899 `numYear` es -1 y para establecer el año 2000 `numYear` es 100.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getFullYear (método, Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear (método, Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear (método, Date)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear (método, Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear (Método, Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)