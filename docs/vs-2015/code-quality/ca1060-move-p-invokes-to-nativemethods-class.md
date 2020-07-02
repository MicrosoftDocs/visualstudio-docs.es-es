---
title: 'CA1060: Move P-invoca a la clase NativeMethods | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e01ad9fc4fc57917c123404d8863d04240585793
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533437"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Mueva P/Invokes a la clase NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|Identificador de comprobación|CA1060|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método usa servicios de invocación de plataforma para tener acceso a código no administrado y no es miembro de una de las clases **NativeMethods** .

## <a name="rule-description"></a>Descripción de la regla
 Los métodos de invocación de plataforma, como los que están marcados con el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo, o los métodos que se definen mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , tienen acceso al código no administrado. Estos métodos deben estar en una de las clases siguientes:

- **NativeMethods** : esta clase no suprime los recorridos de pila para el permiso de código no administrado. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> no se debe aplicar a esta clase). Esta clase es para los métodos que se pueden usar en cualquier lugar porque se realizará un recorrido de pila.

- **SafeNativeMethods** : esta clase suprime los recorridos de pila para el permiso de código no administrado. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase). Esta clase es para los métodos seguros para que cualquier usuario llame a. Los autores de llamadas de estos métodos no son necesarios para realizar una revisión de seguridad completa para asegurarse de que el uso es seguro porque los métodos son inofensivos para cualquier llamador.

- **UnsafeNativeMethods** : esta clase suprime los recorridos de pila para el permiso de código no administrado. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase). Esta clase es para los métodos que son potencialmente peligrosos. Cualquier llamador de estos métodos debe realizar una revisión de seguridad completa para asegurarse de que el uso es seguro porque no se realizará ningún recorrido de pila.

  Estas clases se declaran como `internal` ( `Friend` , en Visual Basic) y declaran un constructor privado para evitar que se creen instancias nuevas. Los métodos de estas clases deben ser `static` y `internal` ( `Shared` y `Friend` en Visual Basic).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, mueva el método a la clase **NativeMethods** adecuada. Para la mayoría de las aplicaciones, el movimiento de P/Invoke a una nueva clase denominada **NativeMethods** es suficiente.

 Sin embargo, si está desarrollando bibliotecas para usarlas en otras aplicaciones, considere la posibilidad de definir otras dos clases que se llamen como **SafeNativeMethods** y **UnsafeNativeMethods**. Estas clases se asemejan a la clase **NativeMethods** ; sin embargo, se marcan con un atributo especial denominado **SuppressUnmanagedCodeSecurityAttribute**. Cuando se aplica este atributo, el tiempo de ejecución no realiza un recorrido de pila completo para asegurarse de que todos los llamadores tienen el permiso **UnmanagedCode** . Normalmente, el tiempo de ejecución comprueba este permiso en el inicio. Dado que la comprobación no se realiza, puede mejorar considerablemente el rendimiento de las llamadas a estos métodos no administrados, también permite que el código con permisos limitados llame a estos métodos.

 Sin embargo, debe usar este atributo con mucha atención. Puede tener implicaciones de seguridad graves si se implementa incorrectamente.

 Para obtener información sobre cómo implementar los métodos, vea el ejemplo de **NativeMethods** , el ejemplo de **SafeNativeMethods** y el ejemplo de **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se declara un método que infringe esta regla. Para corregir la infracción, el **RemoveDirectory** P/Invoke debe moverse a una clase adecuada que esté diseñada para contener solo p/Invoke.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Ejemplo de NativeMethods

### <a name="description"></a>Descripción
 Dado que la clase **NativeMethods** no debe marcarse mediante **SuppressUnmanagedCodeSecurityAttribute**, P/Invokes que se colocan en ella necesitará el permiso **UnmanagedCode** . Dado que la mayoría de las aplicaciones se ejecutan desde el equipo local y se ejecutan con plena confianza, esto no suele ser un problema. Sin embargo, si está desarrollando bibliotecas reutilizables, considere la posibilidad de definir una clase **SafeNativeMethods** o **UnsafeNativeMethods** .

 En el ejemplo siguiente se muestra un método **Interaction. Beep** que ajusta la función **MessageBeep** de user32.dll. **MessageBeep** P/Invoke se coloca en la clase **NativeMethods** .

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Ejemplo de SafeNativeMethods

### <a name="description"></a>Descripción
 Los métodos P/Invoke que se pueden exponer de forma segura a cualquier aplicación y que no tienen ningún efecto secundario deben colocarse en una clase denominada **SafeNativeMethods**. No tiene que solicitar permisos y no tiene que prestar mucha atención a la ubicación desde la que se les llama.

 En el ejemplo siguiente se muestra una propiedad **Environment. TickCount** que contiene la función **GetTickCount** de kernel32.dll.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Ejemplo de UnsafeNativeMethods

### <a name="description"></a>Descripción
 Los métodos P/Invoke a los que no se puede llamar de manera segura y que podrían provocar efectos secundarios deberían colocarse en una clase denominada **UnsafeNativeMethods**. Estos métodos deben comprobarse rigurosamente para asegurarse de que no se exponen al usuario de forma involuntaria. La regla [CA2118: revisar el uso de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) puede ayudarle con esto. Como alternativa, los métodos deben tener otro permiso exigido en lugar de **UnmanagedCode** cuando los usan.

 En el ejemplo siguiente se muestra un método **cursor. Hide** que contiene la función **ShowCursor** de user32.dll.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Consulte también
 [Advertencias de diseño](../code-quality/design-warnings.md)
