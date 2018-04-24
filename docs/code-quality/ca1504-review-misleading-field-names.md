---
title: 'CA1504: Revise los nombres de campos erróneos'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0caf5e8c158f2c434bd20e4b033ed1e2f7f37e5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
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