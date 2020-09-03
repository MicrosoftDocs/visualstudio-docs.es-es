---
title: 'CA1707: los identificadores no deben contener guiones bajos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe6b90ef971bd00392381f47860d85f34e10dc26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544032"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Los identificadores no deben contener caracteres de subrayado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1707: los identificadores no deben contener guiones bajos](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|Elemento|Value|
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|Identificador de comprobación|CA1707|
|Category|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se produce en ensamblados<br /><br /> No problemático: cuando se produce en parámetros de tipo|

## <a name="cause"></a>Causa
 El nombre de un identificador contiene el carácter de subrayado (_).

## <a name="rule-description"></a>Descripción de la regla
 Por convención, los nombres del identificador no contienen el carácter de subrayado (_). La regla comprueba los espacios de nombres, los tipos, los miembros y los parámetros.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite todos los caracteres de subrayado del nombre.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
