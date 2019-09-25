---
title: 'CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fbc3fbeac6d01b718af2022a09bddb92e9c7c2c6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234573"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|Identificador de comprobación|CA1500|
|Categoría|Microsoft. mantenibilidad|
|Cambio importante|Cuando se desencadena en un parámetro que tiene el mismo nombre que un campo:<br /><br /> -No interrumpir: Si el campo y el método que declara el parámetro no se pueden considerar fuera del ensamblado, independientemente del cambio que realice.<br />-Break: Si cambia el nombre del campo y puede verse fuera del ensamblado.<br />-Break: Si cambia el nombre del parámetro y el método que lo declara puede verse fuera del ensamblado.<br /><br /> Cuando se desencadena en una variable local que tiene el mismo nombre que un campo:<br /><br /> -No interrumpir: Si el campo no se puede visualizar fuera del ensamblado, independientemente del cambio que realice.<br />-No problemático: Si cambia el nombre de la variable local y no cambia el nombre del campo.<br />-Break: Si cambia el nombre del campo y puede verse fuera del ensamblado.|

## <a name="cause"></a>Motivo

Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo. Para detectar las variables locales que infringen la regla, el ensamblado probado se debe compilar con la información de depuración y el archivo de base de datos de programa (. pdb) asociado debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla

Cuando el nombre de un campo de instancia coincide con un parámetro o con un nombre de variable local, se tiene acceso al campo `this` de`Me` instancia [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]mediante la palabra clave (in) cuando está dentro del cuerpo del método. Al mantener el código, es fácil olvidar esta diferencia y suponer que el parámetro o la variable local hace referencia al campo de instancia, lo que conduce a errores. Esto se aplica especialmente a los cuerpos de método largos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el nombre del parámetro o la variable, o bien del campo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran dos infracciones de la regla.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]