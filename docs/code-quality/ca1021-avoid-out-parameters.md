---
title: "CA1021: Evitar par&#225;metros out | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1021"
  - "AvoidOutParameters"
helpviewer_keywords: 
  - "AvoidOutParameters"
  - "CA1021"
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1021: Evitar par&#225;metros out
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOutParameters|  
|Identificador de comprobación|CA1021|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método público o protegido en un tipo público tiene un parámetro `out`.  
  
## Descripción de la regla  
 Para pasar tipos por referencia \(utilizando `out` o `ref`\) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos con múltiples valores devueltos.  Además, no se suele saber qué diferencia hay entre los parámetros `out` y `ref`.  
  
 Cuando se pasa un tipo de referencia "por referencia", el método intenta utilizar el parámetro para devolver una instancia diferente del objeto.  Pasar por referencia un tipo de referencia también se conoce como utilizar un puntero doble, un puntero a un puntero, o el direccionamiento indirecto doble.  Al utilizar la convención de llamada predeterminada, que es pasa "por valor", un parámetro que toma un tipo de referencia recibe un puntero para el objeto.  Se pasa el puntero por valor, no el objeto al que señala.  Pasar por valor quiere decir que el método no puede modificar el puntero para que señale a una instancia nueva del tipo de referencia.  Sin embargo, puede cambiar el contenido del objeto al que señala.  En la mayoría de las aplicaciones, esto es suficiente y provoca el comportamiento deseado.  
  
 Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para lograrlo.  Vea la clase <xref:System.String?displayProperty=fullName> para obtener múltiples métodos que funcionan en cadenas y devuelven una nueva instancia de una cadena.  Cuando se usa este modelo, el llamador debe decidir si mantiene el objeto original.  
  
 Aunque los valores devueltos son comunes y muy utilizados, la aplicación correcta de los parámetros `out` y `ref` requiere un diseño intermedio y conocimiento del código.  Los arquitectos de la biblioteca cuyos diseños están destinados a los usuarios en general no deben esperar que los usuarios dominen el uso de los parámetros `out` o `ref`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla producida por un tipo de valor, obligue al método a devolver el objeto como su valor devuelto.  Si el método debe devolver varios valores, vuelva a diseñarlo para devolver una instancia única de un objeto que contiene los valores.  
  
 Para corregir esta infracción de esta regla producida por un tipo de referencia, asegúrese de que el comportamiento deseado es que devuelva una nueva instancia de la referencia.  Si es así, el método debe utilizar su valor devuelto para ello.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla.  Sin embargo, este diseño podría provocar problemas en la utilidad.  
  
## Ejemplo  
 La siguiente biblioteca muestra dos implementaciones de una clase que genera respuestas a las indicaciones de un usuario.  La primera implementación \(`BadRefAndOut`\) fuerza al usuario de la biblioteca a administrar tres valores devueltos.  La segunda implementación \(`RedesignedRefAndOut`\) reduce la experiencia del usuario devolviendo una instancia de la clase contenedora \(`ReplyData`\) que administra los datos como una sola unidad.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## Ejemplo  
 La aplicación siguiente muestra la experiencia del usuario.  La llamada a la biblioteca rediseñada \(método `UseTheSimplifiedClass` \) es más sencilla y la información devuelta por el método se administra con facilidad.  El resultado de los dos métodos es idéntico.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## Ejemplo  
 El siguiente ejemplo de biblioteca muestra cómo se utilizan los parámetros `ref` para los tipos de referencia y muestra una manera mejor de implementar esta funcionalidad.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## Ejemplo  
 La aplicación siguiente llama a cada método de la biblioteca para mostrar el comportamiento.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Cambiar el puntero, pasado por valor:**  
**12345**  
**12345**  
**Cambiar el puntero, pasado por referencia:**  
**12345**  
**12345 ABCDE**  
**Pasar el valor devuelto:**  
**12345 ABCDE**   
## Métodos del modelo Try  
  
### Descripción  
 Los métodos que implementan el modelo de **Intentar\<Algo\>** , como <xref:System.Int32.TryParse%2A?displayProperty=fullName>, no provocan esta infracción.  En el ejemplo siguiente se muestra una estructura \(tipo de valor\) que implementa el método <xref:System.Int32.TryParse%2A?displayProperty=fullName>.  
  
### Código  
 [!code-cs[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]  
  
## Reglas relacionadas  
 [CA1045: No pasar tipos por referencia](../code-quality/ca1045-do-not-pass-types-by-reference.md)