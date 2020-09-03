---
title: 'CA2207: inicializar campos estáticos de tipo de valor insertados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792fe18a4f472d0b8a4fd62c652f2ae34fcf6864
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546307"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializar campos estáticos de tipo de valor insertados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|Identificador de comprobación|CA2207|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo de valor declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se declara un tipo de valor, se somete a una inicialización predeterminada en la que todos los campos de tipo de valor se establecen en cero y todos los campos de tipo de referencia se establecen en `null` ( `Nothing` en Visual Basic). Solo se garantiza que un constructor estático explícito se ejecute antes de que se llame a un constructor de instancia o a un miembro estático del tipo. Por consiguiente, si el tipo se crea sin llamar a un constructor de instancia, no se garantiza que el constructor estático se ejecute.

 Si todos los datos estáticos se inicializan en línea y no se declara ningún constructor estático explícito, los compiladores de C# y Visual Basic agregan la `beforefieldinit` marca a la definición de clase de MSIL. Los compiladores también agregan un constructor estático privado que contiene el código de inicialización estático. Se garantiza que este constructor estático privado se ejecutará antes de tener acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declare y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1810: Inicializar campos estáticos de tipo de referencia insertados](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
