---
title: 'CA2233: Las operaciones no deben desbordarse | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0531a739ec00c3e6224ef5caa7b1c0bf71f0e4e4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697953"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Las operaciones no deben desbordarse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|Identificador de comprobación|CA2233|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un método realiza una operación aritmética y no valida los operandos de antemano para evitar el desbordamiento.

## <a name="rule-description"></a>Descripción de la regla
 No se deben realizar operaciones aritméticas sin validar primero los operandos para asegurarse de que el resultado de la operación no está fuera del intervalo de valores posibles para los tipos de datos implicados. Según el contexto de ejecución y los tipos de datos implicados, puede dar lugar a un desbordamiento aritmético en ya sea un <xref:System.OverflowException?displayProperty=fullName> o se descartan los bits más significativos del resultado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, valide los operandos antes de realizar la operación.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si los valores posibles de los operandos nunca hará que la operación aritmética de desbordamiento.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 Un método en el siguiente ejemplo manipula un entero que infringe esta regla. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] requiere el **quitar** opción desbordamiento de enteros deshabilitará para que esta activación.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Comentarios
 Si se pasa al método en este ejemplo <xref:System.Int32.MinValue?displayProperty=fullName>, la operación sufriría un subdesbordamiento. Esto hace que el bit más significativo del resultado que se descarten. El código siguiente muestra cómo se produce esto.

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
 El ejemplo siguiente corrige la infracción anterior al validar el valor de entrada.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Corregir con un bloque activado

### <a name="description"></a>Descripción
 El ejemplo siguiente corrige la infracción anterior ajustando la operación en un bloque activado. Si la operación provoca un desbordamiento, un <xref:System.OverflowException?displayProperty=fullName> se iniciará.

 Tenga en cuenta que no se admiten los bloques comprobados en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Activar el desbordamiento y subdesbordamiento aritmético activado
 Si activa activado desbordamiento y subdesbordamiento aritmético en C#, es equivalente a cada operación de enteros de ajuste en un bloque activado.

 **Para activar comprueba el desbordamiento y subdesbordamiento aritmético en C#**

1. En **el Explorador de soluciones**, haga clic en el proyecto y elija **propiedades**.

2. Seleccione la pestaña **Compilar** y haga clic en **Opciones avanzadas**.

3. Seleccione **comprobación de desbordamiento y subdesbordamiento aritmético** y haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
 <xref:System.OverflowException?displayProperty=fullName> [Operadores de C#](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked y Unchecked](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
