---
title: 'CA1725: Los nombres de parámetro deberían coincidir con la declaración base | Microsoft Docs'
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
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7ee2253d01f219bb427d3b23d67112c13c71a86
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206900"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Los nombres de parámetro deberían coincidir con la declaración base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|Identificador de comprobación|CA1725|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un parámetro en un reemplazo de método visible externamente no coincide con el nombre del parámetro en la declaración del método base, o el nombre del parámetro en la declaración del método de interfaz.

## <a name="rule-description"></a>Descripción de la regla
 El uso del mismo nombre para un parámetro en una jerarquía de reemplazo aumenta la utilidad de los reemplazos de método. Cuando el nombre de un parámetro en un método derivado es distinto del nombre de la declaración base, puede resultar difícil determinar si el método es un reemplazo del método base o una nueva sobrecarga del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nombre del parámetro para que coincida con la declaración base. La solución es un cambio importante para los métodos COM visibles.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla excepto para los métodos visibles COM en las bibliotecas que se han enviado anteriormente.



