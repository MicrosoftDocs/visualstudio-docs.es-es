---
title: 'CA1504: Revisar los nombres de campos erróneos'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31c147c67854dd59f1fb7c9202f553edfb4a77a8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234504"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Revisar los nombres de campos erróneos

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|Identificador de comprobación|CA1504|
|Categoría|Microsoft. mantenibilidad|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
El nombre de un campo de instancia comienza por "s_" o el nombre de `static` un`Shared` campo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)](en) comienza por "m_".

## <a name="rule-description"></a>Descripción de la regla
Muchos usuarios asocian los nombres de campo que empiezan por "s_" a los datos estáticos. Del mismo modo, los nombres de campo que empiezan por "m_" están asociados a datos de instancia (miembro). Para que el código sea más fácil de mantener, los nombres deben seguir las convenciones de uso general.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el nombre del campo con el prefijo adecuado. Como alternativa, haga que el campo esté de acuerdo con el sufijo actual agregando `static` o quitando el modificador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.