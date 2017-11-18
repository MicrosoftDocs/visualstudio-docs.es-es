---
title: "toLocaleLowerCase (método, String) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>toLocaleLowerCase (Método, String de JavaScript)
Convierte todos los caracteres alfabéticos en minúsculas, teniendo en cuenta la configuración regional actual del entorno de host.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `stringVar` referencia es un `String` objeto o literal de cadena.  
  
 El `toLocaleLowerCase` método convierte los caracteres de una cadena, teniendo en cuenta la configuración regional actual del entorno de host. En la mayoría de los casos, el resultado es el mismo que el resultado de la `toLowerCase` método. Los resultados difieren si las reglas de un lenguaje entran en conflicto con las asignaciones de mayúsculas normales de Unicode.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toLocaleUpperCase (método, String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase (Método)](../../javascript/reference/tolowercase-method-javascript.md)