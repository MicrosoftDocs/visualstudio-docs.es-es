---
title: 'CA2233: Las operaciones no deben desbordarse'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93d4fc872f14a63eeec446d8e6d1f9a2c7acf7ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Las operaciones no deben desbordarse
|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|Identificador de comprobación|CA2233|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un método realiza una operación aritmética y no valida los operandos con antelación para evitar el desbordamiento.

## <a name="rule-description"></a>Descripción de la regla
 No se deberían realizar operaciones aritméticas sin validar primero los operandos para asegurarse de que el resultado de la operación no está fuera del intervalo de valores posibles para los tipos de datos implicados. Según el contexto de ejecución y los tipos de datos implicados, puede dar lugar a un desbordamiento aritmético en la vista una <xref:System.OverflowException?displayProperty=fullName> o se descartan los bits más significativos del resultado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, valide los operandos antes de realizar la operación.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si los valores posibles de los operandos nunca hará que la operación aritmética de desbordamiento.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 Un método en el siguiente ejemplo manipula un entero que infringe esta regla. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requiere la **quitar** opción de desbordamiento de enteros en deshabilitado para que los que se activan.

### <a name="code"></a>Código
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

### <a name="comments"></a>Comentarios
 Si se pasa al método en este ejemplo <xref:System.Int32.MinValue?displayProperty=fullName>, la operación sufriría un subdesbordamiento. Esto hace que el bit más significativo del resultado que se descarte. El código siguiente muestra cómo se produce esto.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Salida

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Corregir con validación de parámetros de entrada

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior al validar el valor de entrada.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Corregir con un bloque comprobado

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior al ajustar la operación en un bloque comprobado. Si la operación provoca un desbordamiento, un <xref:System.OverflowException?displayProperty=fullName> se iniciará.

 Tenga en cuenta que los bloques comprobados no se admiten en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Activar el desbordamiento y subdesbordamiento aritmético comprobado
 Si activa comprobado desbordamiento y subdesbordamiento aritmético en C#, es equivalente a cada operación de entero de ajuste en un bloque comprobado.

 **Para activar comprueba el desbordamiento y subdesbordamiento aritmético en C#**

1.  En **el Explorador de soluciones**, haga clic en el proyecto y elija **propiedades**.

2.  Seleccione la pestaña **Compilar** y haga clic en **Opciones avanzadas**.

3.  Seleccione **comprobación de desbordamiento y subdesbordamiento aritmético** y haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
 <xref:System.OverflowException?displayProperty=fullName> [Operadores de C#](/dotnet/csharp/language-reference/operators/index) [Checked y Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)