---
title: "CA1045: No pasar tipos por referencia | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
helpviewer_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1045: No pasar tipos por referencia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|Identificador de comprobación|CA1045|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método público o protegido de un tipo público tiene un parámetro `ref` que toma un tipo primitivo, un tipo de referencia o un tipo de valor que no es uno de los tipos integrados.  
  
## Descripción de la regla  
 Para pasar tipos por referencia \(utilizando los parámetros `out` o `ref`\) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos que tienen varios valores devueltos.  Además, no se suele saber qué diferencia hay entre los parámetros `out` y `ref`.  
  
 Cuando se pasa un tipo de referencia "por referencia", el método intenta utilizar el parámetro para devolver una instancia diferente del objeto. Pasar por referencia un tipo de referencia también se conoce como utilizar un puntero doble, un puntero a un puntero, o el direccionamiento indirecto doble. Al utilizar la convención de llamada predeterminada, que es pasa "por valor", un parámetro que toma un tipo de referencia recibe un puntero al objeto.  Se pasa el puntero por valor, no el objeto al que señala.  Pasar por valor significa que el método no puede cambiar el puntero para que señale a una nueva instancia del tipo de referencia, pero sí puede modificar el contenido del objeto al que señala.  Para la mayoría de las aplicaciones, esto es suficiente y provoca el comportamiento deseado.  
  
 Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para lograrlo.  Vea la clase <xref:System.String?displayProperty=fullName> para obtener múltiples métodos que funcionan en cadenas y devuelven una nueva instancia de una cadena.  Con este modelo, se deja al llamador que decida si se conserva el objeto original o no.  
  
 Aunque los valores devueltos son comunes y muy utilizados, la aplicación correcta de los parámetros `out` y `ref` requiere un diseño intermedio y conocimiento del código.  Los arquitectos de la biblioteca cuyos diseños están destinados a los usuarios en general no deben esperar que los usuarios dominen el uso de los parámetros `out` o `ref`.  
  
> [!NOTE]
>  Si trabaja con parámetros que son estructuras largas, los recursos adicionales necesarios para copiar estas estructuras pueden afectar al rendimiento cuando se pasan por valor.  En estos casos, podría considerar usar los parámetros `ref` o `out`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla producida por un tipo de valor, obligue al método a devolver el objeto como su valor devuelto.  Si el método debe devolver varios valores, vuelva a diseñarlo para devolver una instancia única de un objeto que contiene los valores.  
  
 Para corregir una infracción de esta regla producida por un tipo de referencia, asegúrese de que el comportamiento deseado es que devuelva una nueva instancia de la referencia.  Si es así, el método debe utilizar su valor devuelto para ello.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir advertencias de esta regla; sin embargo, este diseño podría provocar problemas de uso.  
  
## Ejemplo  
 La siguiente biblioteca muestra dos implementaciones de una clase que genera respuestas a las indicaciones del usuario.  La primera implementación \(`BadRefAndOut`\) fuerza al usuario de la biblioteca a administrar tres valores devueltos.  La segunda implementación \(`RedesignedRefAndOut`\) reduce la experiencia del usuario devolviendo una instancia de la clase contenedora \(`ReplyData`\) que administra los datos como una sola unidad.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## Ejemplo  
 La aplicación siguiente muestra la experiencia del usuario.  La llamada a la biblioteca rediseñada \(método `UseTheSimplifiedClass`\) es más sencilla y la información devuelta por el método se administra con facilidad.  El resultado de los dos métodos es idéntico.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## Ejemplo  
 El siguiente ejemplo de biblioteca muestra cómo se utilizan los parámetros `ref` para los tipos de referencia, y muestra una manera mejor de implementar esta funcionalidad.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## Ejemplo  
 La aplicación siguiente llama a cada método de la biblioteca para mostrar el comportamiento.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Cambiar el puntero, pasado por valor:**  
**12345**  
**12345**  
**Cambiar el puntero, pasado por referencia:**  
**12345**  
**12345 ABCDE**  
**Pasar el valor devuelto:**  
**12345 ABCDE**   
## Reglas relacionadas  
 [CA1021: Evitar parámetros out](../code-quality/ca1021-avoid-out-parameters.md)