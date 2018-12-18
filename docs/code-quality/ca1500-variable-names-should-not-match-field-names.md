---
title: 'CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 74f9cfadc4bc413c3b176d5f37f1017074547435
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548290"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|Identificador de comprobación|CA1500|
|Categoría|Microsoft.Maintainability|
|Cambio problemático|Cuando se desencadena en un parámetro que tiene el mismo nombre que un campo:<br /><br /> No-problemático: si el campo y el método que declara el parámetro no pueden verse fuera del ensamblado, independientemente del cambio que realice.<br />-Importante: si cambia el nombre del campo y se pueden ver desde fuera del ensamblado.<br />-Problemático: si cambia el nombre del parámetro y el método que lo declara puede verse fuera del ensamblado.<br /><br /> Cuando se desencadena en una variable local que tiene el mismo nombre que un campo:<br /><br /> No-problemático: si el campo no puede verse fuera del ensamblado, independientemente del cambio que realice.<br />No-problemático: si cambia el nombre de la variable local y no cambie el nombre del campo.<br />-Problemático: si cambia el nombre del campo y se puede ver desde fuera del ensamblado.|

## <a name="cause"></a>Motivo

Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo. Para capturar las variables locales que infringen la regla, se debe generar el ensamblado probado utilizando la información de depuración y el archivo de programa asociado (.pdb) de la base de datos debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla

Cuando el nombre de un campo de instancia coincide con un parámetro o un nombre de variable local, el campo de instancia se accede mediante el `this` (`Me` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) la palabra clave cuando se encuentra dentro del cuerpo del método. Al mantener el código, es fácil olvidarse de esta diferencia y se supone que el parámetro o la variable local hace referencia al campo de instancia, lo que conduce a errores. Esto sucede especialmente para los cuerpos de método más largo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el nombre de la variable de parámetros o el campo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra dos infracciones de la regla.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]