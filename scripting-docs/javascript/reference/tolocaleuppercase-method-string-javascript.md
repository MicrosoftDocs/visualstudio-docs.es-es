---
title: toLocaleUpperCase (método, String) (JavaScript) | Documentos de Microsoft
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
- toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640435"
---
# <a name="tolocaleuppercase-method-string-javascript"></a>toLocaleUpperCase (Método, String de JavaScript)
Devuelve una cadena donde todos los caracteres alfabéticos han sido configuración regional actual del entorno convertido a mayúsculas, teniendo en cuenta el host.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `stringVar` referencia es un `String` objeto o literal de cadena.  
  
 El `toLocaleUpperCase` método convierte los caracteres de una cadena, teniendo en cuenta la configuración regional actual del entorno de host. En la mayoría de los casos, el resultado es el mismo como resultado la `toUpperCase` método. Los resultados difieren si las reglas de un lenguaje entran en conflicto con las asignaciones de mayúsculas normales de Unicode.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toLocaleLowerCase (método, String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase (Método, String)](../../javascript/reference/touppercase-method-string-javascript.md)