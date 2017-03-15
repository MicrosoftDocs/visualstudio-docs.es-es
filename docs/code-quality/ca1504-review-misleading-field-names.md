---
title: "CA1504: Revise los nombres de campos err&#243;neos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1504: Revise los nombres de campos err&#243;neos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|Identificador de comprobación|CA1504|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 El nombre de un campo de instancia empieza por "s\_" o el nombre de un campo `static` \(`Shared` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) empieza por "m\_".  
  
## Descripción de la regla  
 Muchos usuarios asocian los nombres de campo que empiezan por "s\_" a datos estáticos.  De manera similar, los nombres de campo que empiezan por "m\_" se asocian a datos de instancia \(miembro\).  Para mantener el código más fácilmente, los nombres deben seguir las convenciones utilizadas generalmente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre del campo y utilice para ello el prefijo adecuado.  O bien, agregue o quite el modificador `static` para que el campo concuerde con el sufijo actual.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.