---
title: 'CA1500: los nombres de variable no deben coincidir con los nombres de campo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9565bc1ae3166c0475e8af7f0fde381497309b01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547919"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1500: los nombres de variables no deben coincidir con los nombres de campo](/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).

|Elemento|Value|
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|Identificador de comprobación|CA1500|
|Category|Microsoft. mantenibilidad|
|Cambio problemático|Cuando se desencadena en un parámetro que tiene el mismo nombre que un campo:<br /><br /> -No interrumpir: Si el campo y el método que declara el parámetro no se pueden considerar fuera del ensamblado, independientemente del cambio que realice.<br />-Break: Si cambia el nombre del campo y puede verse fuera del ensamblado.<br />-Break: Si cambia el nombre del parámetro y el método que lo declara puede verse fuera del ensamblado.<br /><br /> Cuando se desencadena en una variable local que tiene el mismo nombre que un campo:<br /><br /> -No interrumpir: Si el campo no se puede visualizar fuera del ensamblado, independientemente del cambio que realice.<br />-No problemático: Si cambia el nombre de la variable local y no cambia el nombre del campo.<br />-Break: Si cambia el nombre del campo y puede verse fuera del ensamblado.|

## <a name="cause"></a>Causa
 Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo. Para detectar las variables locales que infringen la regla, el ensamblado probado se debe compilar con la información de depuración y el archivo de base de datos de programa (. pdb) asociado debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
 Cuando el nombre de un campo de instancia coincide con un parámetro o con un nombre de variable local, se tiene acceso al campo de instancia mediante la `this` `Me` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] palabra clave (in) cuando está dentro del cuerpo del método. Al mantener el código, es fácil olvidar esta diferencia y suponer que el parámetro o la variable local hace referencia al campo de instancia, lo que conduce a errores. Esto se aplica especialmente a los cuerpos de método largos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nombre del parámetro o la variable, o bien del campo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos infracciones de la regla.

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
