---
title: "CA1407: Evite miembros est&#225;ticos en tipos visibles para COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1407"
  - "AvoidStaticMembersInComVisibleTypes"
helpviewer_keywords: 
  - "CA1407"
  - "AvoidStaticMembersInComVisibleTypes"
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1407: Evite miembros est&#225;ticos en tipos visibles para COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|Identificador de comprobación|CA1407|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo marcado específicamente como visible para el Modelo de objetos componentes \(COM\) contiene un método `public` `static`.  
  
## Descripción de la regla  
 COM no es compatible con métodos `static`.  
  
 Esta regla omite descriptores de acceso de eventos y propiedades, métodos de sobrecarga de operadores o métodos marcados mediante el atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o el atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
 De manera predeterminada, son visibles para COM: ensamblados, tipos públicos, miembros de instancia públicos de tipos públicos y todos los miembros de tipos de valor públicos.  
  
 Para que ocurra esta regla, un <xref:System.Runtime.InteropServices.ComVisibleAttribute> de nivel de ensamblado se debe establecer en `false` y el <xref:System.Runtime.InteropServices.ComVisibleAttribute> de clase se debe establecer en `true`, como se muestra en el código siguiente.  
  
```c#  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## Cómo corregir infracciones  
 Para corregir una infracción a esta regla, cambie el diseño de forma que se utilice un método de instancia que proporcione la misma funcionalidad que el método `static`.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si un cliente COM no necesita acceso a la funcionalidad proporcionada por el método `static`.  
  
## Infracción de ejemplo  
  
### Descripción  
 En el siguiente ejemplo se muestra un método `static` que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### Comentarios  
 En este ejemplo, no se puede llamar al método **Book.FromPages** desde COM.  
  
## Corrección del ejemplo  
  
### Descripción  
 Para corregir la infracción del ejemplo anterior, podría cambiar el método a un método de instancia, pero eso no tiene sentido en esta instancia.  Una solución mejor es aplicar explícitamente `ComVisible(false)` al método para que los demás programadores vean claramente que el método no es visible desde COM.  
  
 En el siguiente ejemplo se aplica <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> al método.  
  
### Código  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## Reglas relacionadas  
 [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: Evite argumentos Int64 para clientes Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## Vea también  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)