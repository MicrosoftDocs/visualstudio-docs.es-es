---
title: 'CA1823: Evitar los campos privados no utilizados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a33d6e0301894b23f4671e16b24ea0b34eac4904
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918499"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitar los campos privados no utilizados
|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|Identificador de comprobación|CA1823|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Esta regla se notifica cuando existe un campo privado en el código, pero no se usa en cualquier ruta de acceso del código.

## <a name="rule-description"></a>Descripción de la regla
 Se detectaron campos privados a los que no parece que se tenga acceso en el ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el campo o agregue código que lo utilice.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)