---
title: 'CA1060: Mover P/Invokes a la clase NativeMethods'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e1dc9cf738e74390ea1867966d20f4246d0b1f8c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874237"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Mover P/Invokes a la clase NativeMethods

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|Identificador de comprobación|CA1060|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un método utiliza servicios de invocación de plataforma para tener acceso a código no administrado y no es un miembro de uno de los **NativeMethods** clases.

## <a name="rule-description"></a>Descripción de la regla

Los métodos de invocación de plataforma, como las que se marcan con el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo o los métodos que se definen mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], tener acceso a código no administrado. Estos métodos deben estar en una de las clases siguientes:

- **NativeMethods** -esta clase no suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> no se debe aplicar a esta clase.) Esta clase es para los métodos que pueden usarse en cualquier lugar porque se realizará un recorrido de pila.

- **SafeNativeMethods** -esta clase suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase.) Esta clase es para los métodos que son seguros llamar a. Los llamadores de estos métodos no tienen que realizar una revisión de seguridad completa para asegurarse de que su uso es seguro porque los métodos son inofensivos para los llamadores.

- **UnsafeNativeMethods** -esta clase suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase.) Esta clase es para los métodos que son potencialmente peligrosos. Cualquier llamador de estos métodos debe realizar una revisión de seguridad completa para asegurarse de que su uso es seguro, ya que no se realizará ningún recorrido de pila.

Estas clases se declaran como `internal` (`Friend`, en Visual Basic) y declarar un constructor privado para impedir que se va a crear nuevas instancias. Los métodos en estas clases deben estar `static` y `internal` (`Shared` y `Friend` en Visual Basic).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, mueva el método correspondiente **NativeMethods** clase. Para la mayoría de las aplicaciones, mover P/Invokes a una nueva clase denominada **NativeMethods** es suficiente.

 Sin embargo, si va a desarrollar bibliotecas para su uso en otras aplicaciones, debe considerar definir otras dos clases se denominan **SafeNativeMethods** y **UnsafeNativeMethods**. Estas clases son similares a los **NativeMethods** clase; sin embargo, se marcan con un atributo especial denominado **SuppressUnmanagedCodeSecurityAttribute**. Cuando se aplica este atributo, el tiempo de ejecución no realiza un recorrido de pila completo para asegurarse de que todos los llamadores tengan el **UnmanagedCode** permiso. Normalmente, el tiempo de ejecución comprueba este permiso al inicio. Dado que no se realiza la comprobación, puede mejorar considerablemente el rendimiento para las llamadas a estos métodos no administrados, también permite código que tiene permisos para llamar a estos métodos limitados.

 Sin embargo, debe utilizar este atributo con mucho cuidado. Puede tener implicaciones de seguridad grave si se implementa incorrectamente...

 Para obtener información sobre cómo implementar los métodos, vea el **NativeMethods** ejemplo, **SafeNativeMethods** ejemplo, y **UnsafeNativeMethods** ejemplo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente declara un método que infringe esta regla. Para corregir la infracción, la **RemoveDirectory** P/Invoke deben moverse a una clase adecuada que está diseñada para contener solo P/Invoke.

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>Ejemplo de NativeMethods

### <a name="description"></a>Descripción
 Dado que el **NativeMethods** no se debe marcar la clase mediante el uso de **SuppressUnmanagedCodeSecurityAttribute**, requerirá P/Invokes se colocan en él **UnmanagedCode** permiso. Dado que la mayoría de las aplicaciones se ejecuta desde el equipo local y ejecuta con plena confianza, esto no suele ser un problema. Sin embargo, si va a desarrollar bibliotecas reutilizables, puede definir un **SafeNativeMethods** o **UnsafeNativeMethods** clase.

 El ejemplo siguiente se muestra un **Interaction.Beep** método que encapsula el **MessageBeep** función desde user32.dll. El **MessageBeep** P/Invoke se coloca en el **NativeMethods** clase.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>Ejemplo de SafeNativeMethods

### <a name="description"></a>Descripción
 Los métodos P/Invoke que se pueden exponer de forma segura a cualquier aplicación y que no tienen efectos secundarios deben colocarse en una clase que se denomina **SafeNativeMethods**. No es necesario solicitar permisos y no tiene mucha atención a donde se les llama desde.

 El ejemplo siguiente se muestra un **Environment.TickCount** propiedad que ajusta la **GetTickCount** función desde kernel32.dll.

### <a name="code"></a>Código
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>Ejemplo de UnsafeNativeMethods

### <a name="description"></a>Descripción
 Los métodos que no se puede llamar de forma segura y que podría provocar efectos secundarios de P/Invoke deben colocarse en una clase que se denomina **UnsafeNativeMethods**. Estos métodos deben comprobarse exhaustivamente para asegurarse de que no se exponen al usuario involuntariamente. La regla [CA2118: Revise el uso de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) puede ayudarle con esto. Como alternativa, los métodos deben tener otro permiso que se requiere en lugar de **UnmanagedCode** cuando usen.

 El ejemplo siguiente se muestra un **Cursor.Hide** método que encapsula el **ShowCursor** función desde user32.dll.

### <a name="code"></a>Código
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>Vea también

- [Advertencias de diseño](../code-quality/design-warnings.md)