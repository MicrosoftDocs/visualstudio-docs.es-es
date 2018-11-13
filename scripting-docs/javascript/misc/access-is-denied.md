---
title: Se denegó el acceso | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9b49f60395a853d7dfda91738ccccaba9d585b46
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295168"
---
# <a name="access-is-denied"></a>Se denegó el acceso
Un script intentó acceder a datos desde un origen diferente del host de la página actual. La Directiva de mismo origen que siguen Internet Explorer y otros exploradores permite a los scripts acceder a datos únicamente de orígenes con el mismo esquema, host y puerto de la dirección URL de la página actual.  
  
 Por ejemplo, si la página actual es `https://employees.mycompany.com`, no se puede tener acceso a datos desde las direcciones URL siguientes:  
  
-   `http://data.contoso.com`, porque usa HTTP en lugar de HTTPS.  
  
-   `https://somedatasource.com`, porque es un dominio diferente.  
  
-   `https://employees.mycompany.com:8888`, porque utiliza un puerto diferente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Investigue si la API a la que intenta llamar admite JSONP o CORS, que son dos métodos que permiten scripting entre orígenes con seguridad.  
  
-   Si intenta llamar a una API de REST, refactorice esta llamada al código del lado servidor y luego exponga un nuevo punto de conexión REST para los scripts del lado cliente.  
  
     Para obtener más información, busque la documentación en línea relacionada con la Directiva de mismo origen, JSONP y CORS.
