---
title: "CA1402: Evite sobrecargas en interfaces visibles para COM | Microsoft Docs"
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
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402: Evite sobrecargas en interfaces visibles para COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|Identificador de comprobación|CA1402|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una interfaz visible para el Modelo de objetos componentes \(COM\) declara métodos sobrecargados.  
  
## Descripción de la regla  
 Cuando se exponen métodos sobrecargados a los clientes COM, sólo la primera sobrecarga de método conserva su nombre.  Las sobrecargas subsiguientes reciben un nombre único resultante de anexar al nombre un carácter de subrayado \('\_'\) y un entero correspondiente al orden de declaración de la sobrecarga.  Por ejemplo, considere los siguientes métodos.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Estos métodos se exponen a los clientes COM como los siguientes.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Los clientes COM de Visual Basic 6 no pueden implementar métodos de interfaz mediante un carácter de subrayado en el nombre.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre de los métodos sobrecargados de modo que sus nombres sean únicos.  Como alternativa, puede hacer que la interfaz sea invisible para COM cambiando la accesibilidad a `internal` \(`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) o aplicando el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false`.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra una interfaz que infringe la regla y otra que la cumple.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## Reglas relacionadas  
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vea también  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/long-data-type)