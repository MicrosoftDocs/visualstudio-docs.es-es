---
title: 'CA1823: Evitar los campos privados sin utilizar'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47a2ad3b64055584551a63a2333e29286783d8cf
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921357"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitar los campos privados sin utilizar

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|Identificador de comprobación|CA1823|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Esta regla se muestra cuando existe un campo privado en el código, pero no se usa en ninguna ruta de código.

## <a name="rule-description"></a>Descripción de la regla
Se detectaron campos privados a los que no parece que se tenga acceso en el ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite el campo o agregue el código que lo usa.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
[CA1812: Evitar clases internas sin instancias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Revisar los parámetros no usados](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Quitar variables locales no usadas](../code-quality/ca1804-remove-unused-locals.md)

[CA1811: Evitar código privado no llamado](../code-quality/ca1811-avoid-uncalled-private-code.md)