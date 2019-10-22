---
title: 'CA1823: evitar campos privados no usados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7ccfbe863e010b4dcf8a9d1b442c9bcdba6822e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661125"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitar los campos privados no utilizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|Identificador de comprobación|CA1823|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Esta regla se muestra cuando existe un campo privado en el código, pero no se usa en ninguna ruta de código.

## <a name="rule-description"></a>Descripción de la regla
 Se detectaron campos privados a los que no parece que se tenga acceso en el ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el campo o agregue el código que lo usa.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)
