---
title: 'CA2233: las operaciones no deben desbordarse | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 70a0bab8cfb3bf14a763f759e0e44a754ad878d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662778"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Las operaciones no deben desbordarse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|Identificador de comprobación|CA2233|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un método realiza una operación aritmética y no valida los operandos con antelación para evitar el desbordamiento.

## <a name="rule-description"></a>Descripción de la regla
 No se deben realizar operaciones aritméticas sin validar primero los operandos para asegurarse de que el resultado de la operación no está fuera del intervalo de valores posibles para los tipos de datos implicados. Dependiendo del contexto de ejecución y de los tipos de datos implicados, el desbordamiento aritmético puede dar como resultado un <xref:System.OverflowException?displayProperty=fullName> o los bits más significativos del resultado descartado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, valide los operandos antes de realizar la operación.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si los valores posibles de los operandos nunca harán que la operación aritmética se desborde.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 Un método en el ejemplo siguiente manipula un entero que infringe esta regla. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] requiere que se deshabilite la opción para **quitar** el desbordamiento de enteros para que se active.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Comentarios
 Si se pasa el método en este ejemplo <xref:System.Int32.MinValue?displayProperty=fullName>, la operación se subdesbordamiento. Esto hace que se descarte el bit más significativo del resultado. En el código siguiente se muestra cómo se produce esto.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 FUSIÓN

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Resultados

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Corrección con validación de parámetros de entrada

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior mediante la validación del valor de Input.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Corregir con un bloque activado

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior ajustando la operación en un bloque activado. Si la operación provoca un desbordamiento, se producirá una <xref:System.OverflowException?displayProperty=fullName>.

 Tenga en cuenta que los bloques comprobados no se admiten en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Activar desbordamiento o subdesbordamiento aritmético comprobados
 Si activa el desbordamiento o subdesbordamiento aritmético comprobados C#en, es equivalente a ajustar cada operación de entero en un bloque activado.

 **Para activar el desbordamiento o subdesbordamiento aritmético comprobados enC#**

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y elija **propiedades**.

2. Seleccione la pestaña **Compilar** y haga clic en **Opciones avanzadas**.

3. Seleccione **Buscar desbordamiento o** subdesbordamiento aritmético y haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
 <xref:System.OverflowException?displayProperty=fullName> [ C# operadores](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [comprobados y desactivados](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
