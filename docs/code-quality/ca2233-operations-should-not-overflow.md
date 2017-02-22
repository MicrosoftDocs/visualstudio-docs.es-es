---
title: "CA2233: Las operaciones no deben desbordarse | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2233: Las operaciones no deben desbordarse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|Identificador de comprobación|CA2233|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un método realiza una operación aritmética y no valida de antemano los operandos para evitar el desbordamiento.  
  
## Descripción de la regla  
 Las operaciones aritméticas no deberían realizarse sin validar primero los operandos para asegurase de que el resultado de la operación no se encuentra fuera del intervalo de valores posible de los tipos de datos que se utilicen.  Según la ejecución del contexto y los tipos de datos que se van a utilizar, el desbordamiento aritmético puede provocar una <xref:System.OverflowException?displayProperty=fullName> o que se descarten los bits más significativos del resultado.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, valide los operandos antes de realizar la operación.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si los valores posibles de los operandos nunca provocasen el desbordamiento de la operación matemática.  
  
## Ejemplo de infracción  
  
### Descripción  
 Un método del siguiente ejemplo manipula un entero que infringe esta regla.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] exige que la opción **Quitar** desbordamiento de enteros esté deshabilitada para que esto desencadene.  
  
### Código  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### Comentarios  
 Si se pasa al método de este ejemplo <xref:System.Int32.MinValue?displayProperty=fullName>, la operación sufriría un subdesbordamiento.  Esto produce el bit más significativo del resultado que se va a descartar.  El código siguiente muestra cómo se produce esto.  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Resultados  
  
```  
2147483647  
```  
  
## Corregir con validación del parámetro de entrada  
  
### Descripción  
 En el ejemplo siguiente se corrige la infracción anterior mediante la validación del valor de entrada.  
  
### Código  
 [!code-cs[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## Corregir con un bloque comprobado  
  
### Descripción  
 En el ejemplo siguiente se corrige la infracción anterior mediante el ajuste de la operación en un bloque comprobado.  Si la operación produce un desbordamiento, se producirá <xref:System.OverflowException?displayProperty=fullName>.  
  
 Observe que los bloques comprobados no se admiten en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### Código  
 [!code-cs[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## Activar el desbordamiento\/subdesbordamiento aritmético comprobado  
 Si activa el desbordamiento\/subdesbordamiento aritmético comprobado en C\#, será equivalente a ajustar cada operación de enteros en un bloque comprobado.  
  
 **Para activar el desbordamiento\/subdesbordamiento aritmético comprobado en C\#**  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y elija **Propiedades**.  
  
2.  Seleccione la pestaña **Compilar** y haga clic en **Avanzadas**.  
  
3.  Seleccione **Comprobar el desbordamiento y subdesbordamiento aritmético** y haga clic en **Aceptar**.  
  
## Vea también  
 <xref:System.OverflowException?displayProperty=fullName>   
 [operadores de C\#](/dotnet/csharp/language-reference/operators/index)   
 [Checked y unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)