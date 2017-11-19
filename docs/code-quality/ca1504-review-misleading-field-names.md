---
title: "CA1504: Revise los nombres de campos erróneos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d03c07b48b2cfbfc19fcb9aa2ac4353ddf87a8a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Revise los nombres de campos erróneos
|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|Identificador de comprobación|CA1504|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 El nombre de un campo de instancia empieza por "s_" o el nombre de un `static` (`Shared` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo empieza por "m_".  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los nombres de campo que empiezan por "s_" están asociados con datos estáticos entre varios usuarios. De forma similar, los nombres de campo que empiezan por "m_" se asocian con los datos de instancia (miembro). Para el código más fácil de mantener, los nombres deben seguir las convenciones utilizadas normalmente.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre del campo mediante el prefijo adecuado. O bien, hacer que el campo de acuerdo con el sufijo actual agregando o quitando la `static` modificador.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.