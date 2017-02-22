---
title: "CA1060: Mueva P/Invokes a la clase NativeMethods | Microsoft Docs"
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
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1060: Mueva P/Invokes a la clase NativeMethods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|Identificador de comprobación|CA1060|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método utiliza los servicios de invocación de plataforma para tener acceso al código no administrado y no es un miembro de una de las clases **NativeMethods**.  
  
## Descripción de la regla  
 Los métodos de invocación de plataforma, como los marcados mediante el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> \(o los métodos definidos utilizando la palabra clave `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) acceden al código no administrado.  Estos métodos deberían estar en una de las clases siguientes:  
  
-   **NativeMethods**: esta clase no suprime los recorridos de pilas para el permiso de código no administrado. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> no se debe aplicar a esta clase.\) Esta clase es para los métodos que se pueden utilizar en cualquier parte porque se realizará un recorrido de pila.  
  
-   **SafeNativeMethods**: esta clase suprime los recorridos de pila para el permiso de código no administrado. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase.\) Esta clase es para los métodos que son seguros para llamar.  Los llamadores de estos métodos no requieren que se realice una revisión completa de seguridad para garantizar que su uso es seguro puesto que los métodos son inofensivos para los llamadores.  
  
-   **UnsafeNativeMethods**: esta clase suprime los recorridos de pila para el permiso de código no administrado. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase.\) Esta clase es para métodos que son potencialmente peligrosos.  Cualquier llamador de estos métodos debe realizar una revisión de seguridad completa para garantizar que su uso es seguro puesto que no se realizará ningún recorrido de pila.  
  
 Estas clases se declaran como `internal` \(`Friend` en Visual Basic\) y declaran un constructor privado para evitar que se creen nuevas instancias.  Los métodos de estas clases deberían ser `static` e `internal` \(`Shared` y `Friend` en Visual Basic\).  
  
## Cómo corregir infracciones  
 Para corregir una infracción a esta regla, mueva el método a la clase **NativeMethods** adecuada.  Para la mayoría de las aplicaciones, basta con mover los elementos P\/Invoke a una nueva clase denominada **NativeMethods**.  
  
 Sin embargo, si va a desarrollar bibliotecas para usarlas en otras aplicaciones, debe considerar la posibilidad de definir otras dos clases denominadas **SafeNativeMethods** y **UnsafeNativeMethods**.  Estas clases se parecen a la clase **NativeMethods**; sin embargo, se marcan mediante un atributo especial denominado **SuppressUnmanagedCodeSecurityAttribute**.  Cuando se aplica este atributo, el motor en tiempo de ejecución no realiza un recorrido de pila completo para asegurarse de que todos los llamadores tienen el permiso **UnmanagedCode**.  El motor en tiempo de ejecución comprueba normalmente este permiso durante el inicio.  Dado que no se realiza la comprobación, se puede mejorar considerablemente el rendimiento de las llamadas a estos métodos no controlados, además de permitir que código con permisos limitados llame a estos métodos.  
  
 Sin embargo, debería utilizar este atributo con gran cuidado.  Puede tener serias implicaciones de seguridad si se implementa incorrectamente.  
  
 Para obtener información sobre cómo implementar los métodos, vea el ejemplo de **NativeMethods**, el ejemplo de **SafeNativeMethods** y el ejemplo de **UnsafeNativeMethods**.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo declara un método que infringe esta regla.  Para corregir la infracción, el elemento P\/Invoke de **RemoveDirectory** se debe mover a una clase adecuada que esté diseñada para almacenar únicamente elementos P\/Invoke.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## Ejemplo de NativeMethods  
  
### Descripción  
 Dado que la clase **NativeMethods** no se debe marcar mediante **SuppressUnmanagedCodeSecurityAttribute**, los elementos P\/Invoke incluidos dentro de ella requerirán el permiso **UnmanagedCode**.  Como la mayoría de las aplicaciones se ejecutan desde el equipo local y conjuntamente con plena confianza, esto no suele suponer un problema.  Sin embargo, si va a desarrollar bibliotecas reutilizables, debe considerar la posibilidad de definir una clase **SafeNativeMethods** o **UnsafeNativeMethods**.  
  
 En el ejemplo siguiente se muestra un método **Interaction.Beep** que contiene la función **MessageBeep** de user32.dll.  El elemento P\/Invoke de **MessageBeep** se coloca en la clase **NativeMethods**.  
  
### Código  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## Ejemplo de SafeNativeMethods  
  
### Descripción  
 Los métodos de P\/Invoke que pueden exponerse a cualquier aplicación sin peligro y que no tienen efectos secundarios se deben colocar en una clase denominada **SafeNativeMethods**.  De esta forma, no tendrá que requerir permisos ni prestar demasiada atención al lugar del que se llaman.  
  
 En el ejemplo siguiente se muestra una propiedad **Environment.TickCount** que contiene la función **GetTickCount** de kernel32.dll.  
  
### Código  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## Ejemplo de UnsafeNativeMethods  
  
### Descripción  
 Los métodos P\/Invoke a los que no se pueden llamar sin riesgo y que podrían producir efectos secundarios se deberían colocar en una clase que se denomina **UnsafeNativeMethods**.  Estos métodos deben comprobarse exhaustivamente para garantizar que no se exponen al usuario involuntariamente.  La regla [CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) puede servir de ayuda para tal fin.  Asimismo, los métodos deben tener otro permiso que se solicita en lugar de **UnmanagedCode** cuando se utilizan.  
  
 En el ejemplo siguiente se muestra un método **Cursor.Hide** que contiene la función **ShowCursor** de user32.dll.  
  
### Código  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## Vea también  
 [Diseñar advertencias](../code-quality/design-warnings.md)