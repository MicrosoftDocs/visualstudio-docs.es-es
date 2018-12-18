---
title: 'CA1504: Revise los nombres de campos erróneos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: dae321a15de10063352a00980879f35e10cfb9bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887328"
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
 Los nombres de campo que empiezan por "s_" están asociados con datos estáticos entre varios usuarios. De forma similar, los nombres de campo que empiezan por "m_" se asocian con datos de instancia (miembro). Para mantener más fácilmente el código, los nombres deben seguir las convenciones de usadas general.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nombre del campo con el prefijo adecuado. Como alternativa, hacer que el campo está de acuerdo con el sufijo actual agregando o quitando la `static` modificador.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.