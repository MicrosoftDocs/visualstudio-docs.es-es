---
title: "CA2105: Los campos de matrices no deber&#237;an ser de solo lectura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2105: Los campos de matrices no deber&#237;an ser de solo lectura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|Identificador de comprobación|CA2105|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un campo público o protegido que contiene una matriz se declara como de sólo lectura.  
  
## Descripción de la regla  
 Cuando se aplica el modificador `readonly` \(`ReadOnly` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) a un campo que contiene una matriz, el campo no se modifica para hacer referencia a una matriz distinta.  Sin embargo, se pueden cambiar los elementos de la matriz almacenados en un campo de solo lectura.  El código que toma decisiones o realiza operaciones basadas en los elementos de una matriz de solo lectura a la que se puede acceder públicamente podría contener una vulnerabilidad de seguridad explotable.  
  
 Observe que al tener un campo público, también se infringe la regla de diseño [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
## Cómo corregir infracciones  
 Para corregir la vulnerabilidad de seguridad identificada por esta regla, no confíe en el contenido de una matriz de solo lectura accesible públicamente.  Se recomienda que realice uno de los procedimientos siguientes:  
  
-   Reemplace la matriz con una colección fuertemente tipada que no se puede cambiar.  Para obtener más información, vea <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.  
  
-   Reemplace el campo público con un método que devuelve un clon de una matriz privada.  Dado que el código no confía en el clon, no hay peligro si se modifican los elementos.  
  
 Si eligiera el segundo método, no reemplace el campo con una propiedad; las propiedades que devuelven matrices afectan negativamente al rendimiento.  Para obtener más información, vea [CA1819: Las propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md).  
  
## Cuándo suprimir advertencias  
 Se desaconseja totalmente excluir una advertencia de esta regla.  Son muy pocos los escenarios en los que el contenido de un campo de solo lectura no sea importante.  Si éste es el caso de su escenario, quite el modificador `readonly` en lugar de excluir el mensaje.  
  
## Ejemplo  
 Este ejemplo muestra los peligros de infringir esta regla.  La primera parte muestra una biblioteca de ejemplo que tiene un tipo, `MyClassWithReadOnlyArrayField`, que contiene dos campos \(`grades` y `privateGrades`\) que no son seguros.  El campo `grades` es público y por consiguiente vulnerable a cualquier llamador.  El campo `privateGrades` es privado pero todavía es vulnerable porque se devuelve a los llamadores por el método `GetPrivateGrades`.  El método `GetSecurePrivateGrades` expone el campo `securePrivateGrades` de forma segura.  Se declara como privado para seguir los procedimientos de diseño recomendados.  La segunda parte muestra el código que cambia los valores almacenados en los miembros `grades` y `privateGrades`.  
  
 En el ejemplo siguiente se incluye la biblioteca de clases de ejemplo.  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## Ejemplo  
 El código siguiente utiliza la biblioteca de clases de ejemplo para mostrar los problemas de seguridad de la matriz de sólo lectura.  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 El resultado de este ejemplo es:  
  
  **Antes de modificar: grados: 90, 90, 90 grados privados: 90, 90, 90 grados seguros, 90, 90, 90**  
**Después de modificar: grados: 90, 555, 90 grados privados: 90, 555, 90 grados seguros, 90, 90, 90**   
## Vea también  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>