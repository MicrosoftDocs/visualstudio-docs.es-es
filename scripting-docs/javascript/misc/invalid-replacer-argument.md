---
title: Argumento de reemplazo no válido | Microsoft Docs
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
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573809"
---
# <a name="invalid-replacer-argument"></a>Argumento reemplazante no válido
Se ha intentado invocar `JSON.stringify` con un argumento que no es válido. El argumento `replacer` debe ser una función o una matriz.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Cambie el argumento `replacer` a una función o una matriz.  
  
## <a name="example"></a>Ejemplo  
 El código de este ejemplo produce un error en tiempo de ejecución porque `memberfilter` es un objeto en lugar de una función o una matriz.  
  
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
 @No__t_1 de [objeto JSON](../../javascript/reference/json-object-javascript.md)  
 @No__t_1 de la [función JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)  
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)