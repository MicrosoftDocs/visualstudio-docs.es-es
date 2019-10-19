---
title: 'CA1504: Revise los nombres de campo engañosos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3f1cca5dd33047a4d19c78013dd535e0e9dd6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607760"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Revise los nombres de campos erróneos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|Identificador de comprobación|CA1504|
|Categoría|Microsoft. mantenibilidad|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 El nombre de un campo de instancia comienza por "s_" o el nombre de un campo `static` (`Shared` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) comienza por "m_".

## <a name="rule-description"></a>Descripción de la regla
 Muchos usuarios asocian los nombres de campo que empiezan por "s_" a los datos estáticos. Del mismo modo, los nombres de campo que empiezan por "m_" están asociados a datos de instancia (miembro). Para que el código sea más fácil de mantener, los nombres deben seguir las convenciones de uso general.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nombre del campo con el prefijo adecuado. También puede hacer que el campo esté de acuerdo con el sufijo actual agregando o quitando el modificador `static`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.
