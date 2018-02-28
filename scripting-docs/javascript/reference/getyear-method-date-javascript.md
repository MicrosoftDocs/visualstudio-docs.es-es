---
title: "getYear (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="getyear-method-date-javascript"></a>getYear (Método, Date de JavaScript)
Obtiene el año de un `Date` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el año.  
  
## <a name="remarks"></a>Comentarios  
  
> [!IMPORTANT]
>  Este método está obsoleto y se proporciona por compatibilidad con versiones anteriores. Use el método `getFullYear` en su lugar.  
  
 En [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]y, a continuación, en las versiones de Internet Explorer a partir de [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], el valor devuelto es el año almacenado menos 1900. Por ejemplo, el año 1899 se devuelve como -1 y el año 2000 se devuelve como 100.  
  
 En [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] a través de [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], en función de la fórmula en el año. Para los años 1900 y 1999, el valor devuelto es un valor de 2 dígitos que represente el año almacenado menos 1900. Para las fechas fuera de ese intervalo, se devuelve el año de 4 dígitos. Por ejemplo, 1996 se devuelve como 96, pero 1825 y 2025 se devuelven como está.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getFullYear (método, Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear (método, Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear (método, Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear (método, Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear (Método, Date)](../../javascript/reference/setyear-method-date-javascript.md)