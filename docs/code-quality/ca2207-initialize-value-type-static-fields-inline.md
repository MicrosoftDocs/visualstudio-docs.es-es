---
title: 'CA2207: Inicializar campos estáticos de tipo de valor insertados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2caeb78af5fed0c74c02c6e3f578fa34e765355
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920369"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializar campos estáticos de tipo de valor insertados

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|Identificador de comprobación|CA2207|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
Un tipo de valor declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
Cuando se declara un tipo de valor, se somete a una inicialización predeterminada en la que todos los campos de tipo de valor se establecen en cero y todos los campos `null` de`Nothing` tipo de referencia se establecen en (en Visual Basic). Solo se garantiza que un constructor estático explícito se ejecute antes de que se llame a un constructor de instancia o a un miembro estático del tipo. Por consiguiente, si el tipo se crea sin llamar a un constructor de instancia, no se garantiza que el constructor estático se ejecute.

Si todos los datos estáticos se inicializan en línea y no se declara ningún constructor estático C# explícito, los compiladores y `beforefieldinit` Visual Basic agregan la marca a la definición de clase MSIL. Los compiladores también agregan un constructor estático privado que contiene el código de inicialización estático. Se garantiza que este constructor estático privado se ejecutará antes de tener acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declare y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
[CA1810: Inicializar campos estáticos de tipo de referencia insertados](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)