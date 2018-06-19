---
title: 'CA2207: Inicializar campos estáticos de tipo de valor insertados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 883e5d842346a0821b54b2b4eacad3cbc92028b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917691"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializar campos estáticos de tipo de valor insertados
|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|Identificador de comprobación|CA2207|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo de valor declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se declara un tipo de valor, se somete a una inicialización predeterminada donde todos los campos de tipo de valor se establecen en cero y todos los campos de tipo de referencia se establecen en `null` (`Nothing` en Visual Basic). Un constructor estático explícito sólo garantiza la ejecución antes de un constructor de instancia o se llama a un miembro estático del tipo. Por lo tanto, si se crea el tipo sin llamar a un constructor de instancia, no se garantiza que el constructor estático para ejecutar.

 Si todos los datos estáticos es inicializado en línea y no se declara ningún constructor estático explícito, los compiladores de C# y Visual Basic agregan el `beforefieldinit` marca a la definición de clase MSIL. Los compiladores de agregan también un constructor estático privado que contiene el código de inicialización estática. Este constructor estático privado se ejecuta siempre antes de que se tiene acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla inicializar todos los datos estáticos cuando se declara y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1810: Inicializar campos estáticos de tipo de referencia insertados](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)