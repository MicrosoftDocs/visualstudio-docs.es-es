---
title: Se denegó el acceso | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9563cafa4895f89253b4073d788240806a86fa2a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077542"
---
# <a name="access-is-denied"></a>Se denegó el acceso
Un script intentó acceder a datos desde un origen diferente del host de la página actual. La Directiva de mismo origen que siguen Internet Explorer y otros exploradores permite a los scripts acceder a datos únicamente de orígenes con el mismo esquema, host y puerto de la dirección URL de la página actual.  
  
 Por ejemplo, si la página actual es `https://employees.mycompany.com`, no se puede tener acceso a datos desde las direcciones URL siguientes:  
  
- `http://data.contoso.com`, porque usa HTTP en lugar de HTTPS.  
  
- `https://somedatasource.com`, porque es un dominio diferente.  
  
- `https://employees.mycompany.com:8888`, porque utiliza un puerto diferente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Investigue si la API a la que intenta llamar admite JSONP o CORS, que son dos métodos que permiten scripting entre orígenes con seguridad.  
  
- Si intenta llamar a una API de REST, refactorice esta llamada al código del lado servidor y luego exponga un nuevo extremo REST para los scripts del lado cliente.  
  
     Para obtener más información, busque la documentación en línea relacionada con la Directiva de mismo origen, JSONP y CORS.
