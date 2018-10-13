---
title: 'CA2207: Inicializar campos estáticos de tipo de valor insertados | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b473dd1a7e19e92858f9bd504ea24da03cca726a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204677"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializar campos estáticos de tipo de valor insertados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|Identificador de comprobación|CA2207|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo de valor declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se declara un tipo de valor, se somete a una inicialización predeterminada donde todos los campos de tipo de valor se establecen en cero y todos los campos de tipo de referencia se establecen en `null` (`Nothing` en Visual Basic). Un constructor estático explícito solo se garantiza para ejecutar antes de un constructor de instancia o se llama al miembro estático del tipo. Por lo tanto, si el tipo se crea sin una llamada a un constructor de instancia, el constructor estático no se garantiza para ejecutar.

 Si todos los datos estáticos está alineada inicializado y no se declara ningún constructor estático explícito, los compiladores de C# y Visual Basic agregan el `beforefieldinit` marca a la definición de clase MSIL. También, los compiladores agregan un constructor estático privado que contiene el código de inicialización estática. Este constructor estático privado se garantiza que se ejecutará antes de que se tiene acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla inicializar todos los datos estáticos cuando se declara y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1810: Inicializar campos estáticos de tipo de referencia insertados](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)



