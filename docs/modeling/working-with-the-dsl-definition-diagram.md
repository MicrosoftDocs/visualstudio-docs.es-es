---
title: "Trabajar con diagramas de definici&#243;n DSL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.diagram"
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "Herramientas de lenguajes específicos de dominio, Bring Tree Here"
  - "Herramientas de lenguajes específicos de dominio, diagrama"
  - "Herramientas de lenguajes específicos de dominio, Show As Class"
  - "Herramientas de lenguajes específicos de dominio, Show Map Lines"
  - "Herramientas de lenguajes específicos de dominio, Split Tree"
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Trabajar con diagramas de definici&#243;n DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El diagrama de una definición de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] es una herramienta importante para definir el lenguaje específico de dominio.  Puede agregar elementos al modelo del dominio y definir relaciones en el diagrama, y puede modificar el diseño del diagrama para hacerlo más legible.  
  
## Diseño del diagrama  
 El diagrama de la definición de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] tiene dos particiones, la partición **Classes and Relationships** \(Clases y relaciones\) y la partición **Diagram Elements** \(Elementos del diagrama\).  La partición **Classes and Relationships** \(Clases y relaciones\) muestra las clases de dominio, las relaciones de dominio y la herencia. La partición **Diagram Elements** \(Elementos del diagrama\) muestra las clases de forma, las clases de conector, las clases de calle y el diagrama del diseñador generado.  
  
 Las clases de dominio pueden aparecer en varias ubicaciones de las particiones **Classes and Relationships** \(Clases y relaciones\).  Una definición de clase de dominio muestra un árbol de herencia si tiene la clase base para las demás clases de dominio, y un árbol de relaciones si es el origen de relaciones de incrustación o referencia.  Los marcadores de posición de las clases de dominio aparecen como los destinos de las relaciones de incrustación o referencia.  De forma predeterminada, los elementos se muestran con el compartimiento **Domain Properties** \(Propiedades del dominio\) contraído.  No muestran la herencia ni las relaciones de incrustación o referencia.  
  
 Cuando se agrega una clase de dominio, aparece en la parte inferior de la partición **Classes and Relationships** \(Clases y relaciones\).  Cuando se agrega una relación de incrustación o referencia, se dibuja debajo y a la derecha de la clase de dominio de origen.  
  
 A medida que se agregan clases de dominio y relaciones, puede resultar difícil encontrar una clase de dominio determinada.  Para buscar una clase de dominio, haga clic con el botón secundario en ella en **DSL Explorer** \(Explorador de DSL\) y, después, haga clic en **Locate in Diagram** \(Ubicar en el diagrama\).  
  
 En las secciones siguientes se describe cómo cambiar la apariencia del diagrama para que sea más fácil de leer.  
  
## Copiar elementos  
 Puede copiar, cortar y pegar elementos en el diagrama de la definición de DSL.  
  
## Acercar o alejar en el diagrama  
 Para acercar o alejar la vista en el diagrama, use la barra de herramientas de **DSL Designer** \(Diseñador de DSL\) para establecer el nivel de zoom.  
  
## Ocultar líneas de asignación  
 Las líneas de asignación son las líneas que se dibujan entre una clase dominio o una relación de dominio y la forma o conector al que se asigna.  Para ocultar las líneas de asignación, haga clic en el botón **Show Map Lines** \(Mostrar líneas de asignación\) en la barra de herramientas de **DSL Designer** \(Diseñador de DSL\).  Para mostrar las líneas, vuelva a hacer clic en el botón.  
  
## Cambiar el diseño del diagrama  
 Puede cambiar el diseño de la partición **Classes and Relationships** \(Clases y relaciones\) de la siguiente manera.  
  
### Expand\/Collapse \(Expandir o contraer\)  
 Puede reducir el tamaño de un elemento de forma de compartimiento que representa una clase de dominio o una forma; para ello, haga clic con el botón secundario en él y haga clic en **Collapse** \(Contraer\).  Así se oculta el compartimiento **Domain Properties** \(Propiedades del dominio\) de la forma.  Para volver a mostrar el compartimiento **Domain Properties** \(Propiedades del dominio\), haga clic con el botón secundario en la forma y haga clic en **Expand** \(Expandir\).  
  
### Move Up\/Down \(Subir o bajar\)  
 Para subir o bajar una clase de dominio o un elemento del diagrama en la partición, haga clic con el botón secundario en el elemento y, después, haga clic en **Move Up** \(Subir\) o **Move Down** \(Bajar\).  Si mueve un elemento de marcador de posición que se muestra como el destino de una referencia de incrustación o referencia, la relación se moverá con él.  
  
### Expand\/Collapse Relationships Tree \(Expandir o contraer el árbol de relaciones\)  
 Si una clase de dominio representa el rol de origen en una relación de incrustación o referencia con otras clases de dominio, puede ocultar las relaciones; para ello, haga clic con el botón secundario en la definición de la clase de dominio y, después, haga clic en **Collapse Relationships Tree** \(Contraer árbol de relaciones\).  Para mostrar las relaciones, haga clic con el botón secundario en el elemento de definición y, después, haga clic en **Expand Relationships Tree** \(Expandir árbol de relaciones\).  
  
### Expand\/Collapse Inheritance Tree \(Expandir o contraer el árbol de herencia\)  
 Si una clase de dominio es la clase base de otras clases de dominio, puede ocultar el árbol de herencia; para ello, haga clic en la definición de la clase de dominio y, después, haga clic en **Collapse Inheritance Tree** \(Contraer árbol de herencia\).  Para mostrar el árbol de herencia, haga clic con el botón secundario en el elemento de definición y, después, haga clic en **Expand Inheritance Tree** \(Expandir árbol de herencia\).  
  
### Bring Tree Here \(Traer árbol aquí\)  
 Para consolidar el diagrama, haga clic con el botón secundario en una clase de dominio de marcador de posición y, después, haga clic en **Bring Tree Here** \(Traer árbol aquí\).  La clase de dominio de marcador de posición se convierte en un elemento de definición y muestra los árboles de herencia y de relaciones.  El elemento de definición anterior se convierte en un elemento de marcador de posición si es el destino de una relación o el elemento secundario en una relación de herencia; de lo contrario, desaparece.  
  
### Split Tree \(Dividir árbol\)  
 Los árboles de herencia o de relaciones se pueden desglosar; para ello, haga clic con el botón secundario en la definición de clase de dominio que los muestra y, después, haga clic en **Split Tree** \(Dividir árbol\).  El elemento de definición se convierte en un elemento de marcador de posición, y la clase de dominio de definición, junto con sus árboles de herencia y de relaciones, se muestran ahora en la parte inferior de la partición.  
  
### Show As Class \(Mostrar como clase\)  
 Si una relación de dominio tiene relaciones derivadas, o si tiene relaciones incrustadas o de referencia con otras relaciones de dominio, puede mostrar la relación como una clase; para ello, haga clic con el botón secundario en la relación y, después, haga clic en **Show As Class** \(Mostrar como clase\).  La relación se mostrará con un compartimiento **Domain Properties** \(Propiedades del dominio\) y mostrará los árboles de herencia y de relaciones.  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)