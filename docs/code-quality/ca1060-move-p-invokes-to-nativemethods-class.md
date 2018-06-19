---
title: 'CA1060: Movimiento P-se invoca a la clase NativeMethods'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6035553f8d3a4518fe99e7800a61f1b5921d947
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900814"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Mueva P/Invokes a la clase NativeMethods
|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|Identificador de comprobación|CA1060|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método utiliza servicios de invocación de plataforma para tener acceso a código no administrado y no es miembro de uno de los **NativeMethods** clases.

## <a name="rule-description"></a>Descripción de la regla
 Métodos de invocación de plataforma, como aquellos marcados con el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo o los métodos que se definen mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], tener acceso a código no administrado. Estos métodos deberían estar en una de las clases siguientes:

-   **Clase NativeMethods** -esta clase no suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> no se debe aplicar a esta clase.) Esta clase es para los métodos que se pueden usar en cualquier parte porque se realizará un recorrido de pila.

-   **UnsafeNativeMethods** -esta clase suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase.) Esta clase es para los métodos que son seguros para llamar a ningún usuario. Los llamadores de estos métodos no tienen que realizar una revisión de seguridad completa para asegurarse de que su uso es seguro porque los métodos son inofensivos para los llamadores.

-   **SafeNativeMethods** -esta clase suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase.) Esta clase es para los métodos que son potencialmente peligrosos. Cualquier llamador de estos métodos debe realizar una revisión de seguridad completa para asegurarse de que el uso es seguro porque no se realizará ningún recorrido de pila.

 Estas clases se declaran como `internal` (`Friend`, en Visual Basic) y declara un constructor privado para evitar que se va a crear nuevas instancias. Los métodos en estas clases deben ser `static` y `internal` (`Shared` y `Friend` en Visual Basic).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, mueva el método correspondientes **NativeMethods** clase. Para la mayoría de las aplicaciones, mover P/Invokes a una nueva clase que se denomina **NativeMethods** es suficiente.

 Sin embargo, si va a desarrollar bibliotecas para usarlas en otras aplicaciones, puede definir otras dos clases que se denominan **UnsafeNativeMethods** y **SafeNativeMethods**. Estas clases son similares a los **NativeMethods** clase; sin embargo, se marcan con un atributo especial denominado **SuppressUnmanagedCodeSecurityAttribute**. Cuando se aplica este atributo, el tiempo de ejecución no realiza un recorrido de pila completo para asegurarse de que todos los llamadores tengan los **UnmanagedCode** permiso. El tiempo de ejecución comprueba normalmente este permiso al inicio. Dado que no se realiza la comprobación, puede mejorar notablemente el rendimiento para las llamadas a estos métodos no administrados, también permite que el código que tenga permisos para llamar a estos métodos limitados.

 Sin embargo, debe utilizar este atributo con sumo cuidado. Puede tener implicaciones de seguridad grave si se implementa incorrectamente...

 Para obtener información sobre cómo implementar los métodos, consulte el **NativeMethods** ejemplo, **UnsafeNativeMethods** ejemplo, y **SafeNativeMethods** ejemplo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se declara un método que infringe esta regla. Para corregir la infracción, la **RemoveDirectory** P/Invoke se debe mover a una clase adecuada que está diseñada para contener solo P/Invoke.

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>Ejemplo de la clase NativeMethods

### <a name="description"></a>Descripción
 Dado que la **NativeMethods** no debe marcarse con clase **SuppressUnmanagedCodeSecurityAttribute**, requerirá P/Invokes se colocan en ella **UnmanagedCode** permiso. Dado que la mayoría de las aplicaciones que se ejecuta desde el equipo local y se ejecuta con plena confianza, esto no suele ser un problema. Sin embargo, si va a desarrollar bibliotecas reutilizables, debería pensar en definir una **UnsafeNativeMethods** o **SafeNativeMethods** clase.

 El ejemplo siguiente muestra un **Interaction.Beep** método que encapsula la **MessageBeep** función desde user32.dll. El **MessageBeep** P/Invoke se coloca en el **NativeMethods** clase.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>Ejemplo de UnsafeNativeMethods

### <a name="description"></a>Descripción
 Métodos de P/Invoke que pueden exponerse de forma segura a cualquier aplicación y que no tienen efectos secundarios se deben colocar en una clase que se denomina **UnsafeNativeMethods**. No es necesario solicitar permisos y no es necesario prestar mucha atención a donde se les llama desde.

 El ejemplo siguiente muestra un **Environment.TickCount** propiedad que contiene el **GetTickCount** función desde kernel32.dll.

### <a name="code"></a>Código
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>Ejemplo de UnsafeNativeMethods

### <a name="description"></a>Descripción
 Métodos de P/Invoke que no se puede llamar sin ningún riesgo y que podría provocar efectos secundarios se deben colocar en una clase que se denomina **SafeNativeMethods**. Estos métodos deben comprobarse exhaustivamente para asegurarse de que no se exponen al usuario involuntariamente. La regla [CA2118: el uso de SuppressUnmanagedCodeSecurityAttribute revisión](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) puede ayudarle con esto. Como alternativa, los métodos deben tener otro permiso que se exige en lugar de **UnmanagedCode** cuando usen.

 El ejemplo siguiente muestra un **Cursor.Hide** método que encapsula la **ShowCursor** función desde user32.dll.

### <a name="code"></a>Código
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>Vea también
 [Advertencias de diseño](../code-quality/design-warnings.md)