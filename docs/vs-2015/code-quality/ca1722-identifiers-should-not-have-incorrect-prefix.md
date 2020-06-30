---
title: 'CA1722: los identificadores no deben tener un prefijo incorrecto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a7f4f932f8e2db9a558d7440d8965ce5924043b8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544487"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Los identificadores no deben tener un prefijo incorrecto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|Identificador de comprobación|CA1722|
|Category|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un identificador tiene un prefijo incorrecto.

## <a name="rule-description"></a>Descripción de la regla
 Por convención, sólo ciertos elementos de programación tienen nombres que comienzan con un prefijo concreto.

 Los nombres de tipo no tienen un prefijo específico y no deben ir precedidos de un ' C '. Esta regla notifica las infracciones de los nombres de tipo como ' CMyClass ' y no notifica las infracciones de los nombres de tipo como ' cache '.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite el prefijo del identificador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1715: Los identificadores deben tener el prefijo correcto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
