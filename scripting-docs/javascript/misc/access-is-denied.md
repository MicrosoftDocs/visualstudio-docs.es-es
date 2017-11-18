---
title: "Se denegó el acceso | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9c097cd09712d19acf5a0e4999b5c7a47469f958
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="access-is-denied"></a>Se denegó el acceso
Un script intentó acceder a datos desde un origen diferente del host de la página actual. La Directiva de mismo origen que siguen Internet Explorer y otros exploradores permite a los scripts acceder a datos únicamente de orígenes con el mismo esquema, host y puerto de la dirección URL de la página actual.  
  
 Por ejemplo, si la página actual es https://employees.mycompany.com, no se puede acceder a datos de las direcciones URL siguientes:  
  
-   http://data.contoso.com, ya que usa HTTP en lugar de HTTPS.  
  
-   https://somedatasource.com, ya que es un dominio diferente.  
  
-   https://employees.mycompany.com:8888, ya que usa un puerto diferente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Investigue si la API a la que intenta llamar admite JSONP o CORS, que son dos métodos que permiten scripting entre orígenes con seguridad.  
  
-   Si intenta llamar a una API de REST, refactorice esta llamada al código del lado servidor y luego exponga un nuevo punto de conexión REST para los scripts del lado cliente.  
  
     Para obtener más información, busque la documentación en línea relacionada con la Directiva de mismo origen, JSONP y CORS.