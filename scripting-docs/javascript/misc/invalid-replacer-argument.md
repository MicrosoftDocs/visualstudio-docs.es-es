---
title: Argumento reemplazante no válido | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46e01a4e6bb989fad2da6f979c79b7aba13df63a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007319"
---
# <a name="invalid-replacer-argument"></a>Argumento reemplazante no válido
Se ha intentado invocar `JSON.stringify` con un argumento que no es válido. El `replacer` argumento debe ser una función o una matriz.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Cambiar el `replacer` argumento a una función o una matriz.  
  
## <a name="example"></a>Ejemplo  
 El código en este ejemplo genera un error de tiempo de ejecución porque `memberfilter` es un objeto en lugar de una función o matriz.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Vea también  
 [Objeto JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse (función)](../../javascript/reference/json-parse-function-javascript.md)   
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)