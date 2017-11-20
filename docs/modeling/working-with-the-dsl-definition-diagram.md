---
title: "Trabajar con el diagrama de definición DSL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f8a60f9c4ca91ff9aac516d21b3a502a2898aff1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="working-with-the-dsl-definition-diagram"></a>Trabajar con diagramas de definición DSL
El diagrama de un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definición es una herramienta importante para definir el lenguaje específico de dominio. Puede agregar elementos al modelo del dominio y definir relaciones en el diagrama, y puede modificar el diseño del diagrama para hacerlo más legible.  
  
## <a name="the-layout-of-the-diagram"></a>Diseño del diagrama  
 El [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] diagrama de definición tiene dos particiones, el **clases y relaciones** partición y la **elementos del diagrama** partición. El **clases y relaciones** partición muestra las clases de dominio, relaciones de dominio y herencia. El **elementos del diagrama** partición muestra las clases de formas, clases de conector, calle clases y el diagrama del diseñador generado.  
  
 Clases de dominio pueden aparecer en varias ubicaciones en el **clases y relaciones** particiones. Una definición de clase de dominio muestra un árbol de herencia si tiene la clase base para las demás clases de dominio, y un árbol de relaciones si es el origen de relaciones de incrustación o referencia. Los marcadores de posición de las clases de dominio aparecen como los destinos de las relaciones de incrustación o referencia. De forma predeterminada, se muestran los elementos de marcador de posición con el **propiedades del dominio** compartimiento contraído. No muestran la herencia ni las relaciones de incrustación o referencia.  
  
 Cuando se agrega una clase de dominio, aparece en la parte inferior de la **clases y relaciones** partición. Cuando se agrega una relación de incrustación o referencia, se dibuja debajo y a la derecha de la clase de dominio de origen.  
  
 A medida que se agregan clases de dominio y relaciones, puede resultar difícil encontrar una clase de dominio determinada. Puede encontrar una clase de dominio con el botón secundario en el **DSL explorador** y, a continuación, haga clic en **buscar en diagrama**.  
  
 En las secciones siguientes se describe cómo cambiar la apariencia del diagrama para que sea más fácil de leer.  
  
## <a name="copying-elements"></a>Copiar elementos  
 Puede copiar, cortar y pegar elementos en el diagrama de la definición de DSL.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>Acercar o alejar en el diagrama  
 También puede acercar o alejar el diagrama mediante el uso de la **diseñador DSL** barra de herramientas para establecer el nivel de zoom.  
  
## <a name="hiding-map-lines"></a>Ocultar líneas de asignación  
 Las líneas de asignación son las líneas que se dibujan entre una clase dominio o una relación de dominio y la forma o conector al que se asigna. Puede ocultar las líneas de mapa, haga clic en el **mostrar líneas de mapa** situado en la **diseñador DSL** barra de herramientas. Para mostrar las líneas, vuelva a hacer clic en el botón.  
  
## <a name="changing-the-diagram-layout"></a>Cambiar el diseño del diagrama  
 Puede cambiar el diseño de la **clases y relaciones** de partición como se indica a continuación.  
  
### <a name="expandcollapse"></a>Expand/Collapse (Expandir o contraer)  
 Puede reducir el tamaño de un elemento de la forma de compartimiento que representa una clase de dominio o una forma haciendo clic en él y, a continuación, haga clic en **contraer**. Esto oculta la **propiedades del dominio** compartimento de la forma. Para mostrar la **propiedades del dominio** compartimiento de nuevo, haga clic en la forma y, a continuación, haga clic en **expandir**.  
  
### <a name="move-updown"></a>Move Up/Down (Subir o bajar)  
 Puede mover un elemento de clase o diagrama de dominio hacia arriba o hacia abajo en la partición haciendo clic en el elemento y, a continuación, haga clic en **Subir** o **Bajar**. Si mueve un elemento de marcador de posición que se muestra como el destino de una referencia de incrustación o referencia, la relación se moverá con él.  
  
### <a name="expandcollapse-relationships-tree"></a>Expand/Collapse Relationships Tree (Expandir o contraer el árbol de relaciones)  
 Si una clase de dominio desempeña la función de origen de referencia o incrustar relaciones con otras clases de dominio, puede ocultar las relaciones haciendo clic en la definición de clase de dominio y, a continuación, haga clic en **contraer relaciones árbol**. Para mostrar las relaciones, haga clic en el elemento de la definición y, a continuación, haga clic en **expanda el árbol de relaciones**.  
  
### <a name="expandcollapse-inheritance-tree"></a>Expand/Collapse Inheritance Tree (Expandir o contraer el árbol de herencia)  
 Si una clase de dominio es la clase base de otras clases de dominio, puede ocultar el árbol de herencia haciendo clic en la definición de clase de dominio y, a continuación, haga clic en **árbol de herencia de contraer**. Para mostrar el árbol de herencia, haga clic en el elemento de la definición y, a continuación, haga clic en **expanda el árbol de herencia**.  
  
### <a name="bring-tree-here"></a>Bring Tree Here (Traer árbol aquí)  
 Puede consolidar el diagrama haciendo clic en una clase de dominio de marcador de posición y, a continuación, haga clic en **poner árbol aquí**. La clase de dominio de marcador de posición se convierte en un elemento de definición y muestra los árboles de herencia y de relaciones. El elemento de definición anterior se convierte en un elemento de marcador de posición si es el destino de una relación o el elemento secundario en una relación de herencia; de lo contrario, desaparece.  
  
### <a name="split-tree"></a>Split Tree (Dividir árbol)  
 Puede dividir los árboles de herencia o relaciones haciendo clic en la definición de clase de dominio que se muestra y, a continuación, haga clic en **división árbol**. El elemento de definición se convierte en un elemento de marcador de posición, y la clase de dominio de definición, junto con sus árboles de herencia y de relaciones, se muestran ahora en la parte inferior de la partición.  
  
### <a name="show-as-class"></a>Show As Class (Mostrar como clase)  
 Si una relación de dominio tiene derivados relaciones, o si tiene relaciones de incrustación o referencia con otras relaciones de dominio, puede mostrar la relación como una clase haciendo clic en la relación y, a continuación, haga clic en **mostrar como clase** . La relación se mostrarán con un **propiedades del dominio** compartimiento y mostrará los árboles de herencia y relaciones.  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)