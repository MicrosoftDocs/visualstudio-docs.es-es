---
title: Trabajar con diagramas de definición DSL | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd4b15fb7c0f1cbc0630779ecef0373977bb2056
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694218"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Trabajar con diagramas de definición DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El diagrama de un [!INCLUDE[dsl](../includes/dsl-md.md)] definición es una herramienta importante para definir el lenguaje específico de dominio. Puede agregar elementos al modelo del dominio y definir relaciones en el diagrama, y puede modificar el diseño del diagrama para hacerlo más legible.  
  
## <a name="the-layout-of-the-diagram"></a>Diseño del diagrama  
 El [!INCLUDE[dsl](../includes/dsl-md.md)] diagrama de definición tiene dos particiones, el **clases y relaciones** partición y el **elementos del diagrama** partición. El **clases y relaciones** partición muestra las clases de dominio, relaciones de dominio y herencia. El **elementos del diagrama** partición muestra las clases de forma, las clases de conector, las clases de calle y el diagrama del diseñador generado.  
  
 Clases de dominio pueden aparecer en varias ubicaciones en el **clases y relaciones** particiones. Una definición de clase de dominio muestra un árbol de herencia si tiene la clase base para las demás clases de dominio, y un árbol de relaciones si es el origen de relaciones de incrustación o referencia. Los marcadores de posición de las clases de dominio aparecen como los destinos de las relaciones de incrustación o referencia. De forma predeterminada, se muestran los elementos de marcador de posición con el **las propiedades del dominio** contraído del compartimiento. No muestran la herencia ni las relaciones de incrustación o referencia.  
  
 Cuando se agrega una clase de dominio, aparece en la parte inferior de la **clases y relaciones** partición. Cuando se agrega una relación de incrustación o referencia, se dibuja debajo y a la derecha de la clase de dominio de origen.  
  
 A medida que se agregan clases de dominio y relaciones, puede resultar difícil encontrar una clase de dominio determinada. Puede encontrar una clase de dominio con el botón secundario en el **DSL Explorer** y, a continuación, haga clic en **buscar en el diagrama**.  
  
 En las secciones siguientes se describe cómo cambiar la apariencia del diagrama para que sea más fácil de leer.  
  
## <a name="copying-elements"></a>Copiar elementos  
 Puede copiar, cortar y pegar elementos en el diagrama de la definición de DSL.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>Acercar o alejar en el diagrama  
 Puede acercar o alejar el diagrama con el **diseñador DSL** barra de herramientas para establecer el nivel de zoom.  
  
## <a name="hiding-map-lines"></a>Ocultar líneas de asignación  
 Las líneas de asignación son las líneas que se dibujan entre una clase dominio o una relación de dominio y la forma o conector al que se asigna. Puede ocultar las líneas de mapa, haga clic en el **mostrar líneas de mapa** situado en la **diseñador DSL** barra de herramientas. Para mostrar las líneas, vuelva a hacer clic en el botón.  
  
## <a name="changing-the-diagram-layout"></a>Cambiar el diseño del diagrama  
 Puede cambiar el diseño de la **clases y relaciones** de partición como sigue.  
  
### <a name="expandcollapse"></a>Expand/Collapse (Expandir o contraer)  
 Puede reducir el tamaño de un elemento de la forma de compartimiento que representa una clase de dominio o una forma haciendo clic en él y, a continuación, haga clic en **contraer**. Esto oculta la **las propiedades del dominio** compartimento de la forma. Para mostrar el **las propiedades del dominio** compartimiento de nuevo, haga clic en la forma y, a continuación, haga clic en **expandir**.  
  
### <a name="move-updown"></a>Move Up/Down (Subir o bajar)  
 Puede mover un elemento de diagrama o clase de dominio arriba o hacia abajo en la partición haciendo clic en el elemento y, a continuación, haga clic en **Subir** o **Bajar**. Si mueve un elemento de marcador de posición que se muestra como el destino de una referencia de incrustación o referencia, la relación se moverá con él.  
  
### <a name="expandcollapse-relationships-tree"></a>Expand/Collapse Relationships Tree (Expandir o contraer el árbol de relaciones)  
 Si una clase de dominio desempeña el rol de origen en las relaciones de incrustación o referencia con otras clases de dominio, puede ocultar las relaciones haciendo clic en la definición de clase de dominio y, a continuación, haga clic en **contraer árbol de relaciones**. Para mostrar las relaciones, haga clic en el elemento de definición y, a continuación, haga clic en **expandir árbol de relaciones**.  
  
### <a name="expandcollapse-inheritance-tree"></a>Expand/Collapse Inheritance Tree (Expandir o contraer el árbol de herencia)  
 Si una clase de dominio es la clase base de otras clases de dominio, puede ocultar el árbol de herencia haciendo clic en la definición de clase de dominio y, a continuación, haga clic en **contraer árbol de herencia**. Para mostrar el árbol de herencia, haga clic en el elemento de definición y, a continuación, haga clic en **expandir árbol de herencia**.  
  
### <a name="bring-tree-here"></a>Bring Tree Here  
 Puede consolidar el diagrama haciendo clic en una clase de dominio de marcador de posición y, a continuación, haga clic en **Traer árbol aquí**. La clase de dominio de marcador de posición se convierte en un elemento de definición y muestra los árboles de herencia y de relaciones. El elemento de definición anterior se convierte en un elemento de marcador de posición si es el destino de una relación o el elemento secundario en una relación de herencia; de lo contrario, desaparece.  
  
### <a name="split-tree"></a>Split Tree (Dividir árbol)  
 Puede desglosar los árboles de herencia o de relaciones haciendo clic en la definición de clase de dominio que se muestra y, a continuación, haga clic en **dividir árbol**. El elemento de definición se convierte en un elemento de marcador de posición, y la clase de dominio de definición, junto con sus árboles de herencia y de relaciones, se muestran ahora en la parte inferior de la partición.  
  
### <a name="show-as-class"></a>Show As Class  
 Si una relación de dominio tiene relaciones derivadas, o si tiene relaciones de incrustación o referencia con otras relaciones de dominio, puede mostrar la relación como una clase haciendo clic en la relación y, a continuación, haga clic en **mostrar como clase** . La relación se mostrará con un **las propiedades del dominio** compartimiento y mostrará los árboles de herencia y relaciones.  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
