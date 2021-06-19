---
title: Trabajar con diagramas de definición DSL
description: Obtenga información sobre que el diagrama de una definición de herramientas DSL es una herramienta importante para definir un lenguaje específico del dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f401fe0509fc425fff873a7dc224c69359156861
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388079"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Trabajar con diagramas de definición DSL
El diagrama de una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definición es una herramienta importante para definir el lenguaje específico del dominio. Puede agregar elementos al modelo del dominio y definir relaciones en el diagrama, y puede modificar el diseño del diagrama para hacerlo más legible.

## <a name="the-layout-of-the-diagram"></a>Diseño del diagrama
 El [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] diagrama de definición tiene dos particiones, **la partición Clases y relaciones** y la partición Elementos **de** diagrama. La **partición Clases y relaciones muestra** clases de dominio, relaciones de dominio y herencia. La **partición Elementos de** diagrama muestra clases de forma, clases de conector, clases de calle y el diagrama de diseñador generado.

 Las clases de dominio pueden aparecer en varias ubicaciones en las **particiones Clases y** relaciones. Una definición de clase de dominio muestra un árbol de herencia si tiene la clase base para las demás clases de dominio, y un árbol de relaciones si es el origen de relaciones de incrustación o referencia. Los marcadores de posición de las clases de dominio aparecen como los destinos de las relaciones de incrustación o referencia. De forma predeterminada, los elementos de marcador de posición se muestran con el compartimiento **Propiedades del** dominio contraído. No muestran la herencia ni las relaciones de incrustación o referencia.

 Al agregar una clase de dominio, aparece en la parte inferior de la partición **Clases y relaciones.** Cuando se agrega una relación de incrustación o referencia, se dibuja debajo y a la derecha de la clase de dominio de origen.

 A medida que se agregan clases de dominio y relaciones, puede resultar difícil encontrar una clase de dominio determinada. Para encontrar una clase de dominio, haga clic con el botón derecho en ella en el Explorador **dsl y,** a continuación, haga clic **en Buscar en diagrama**.

 En las secciones siguientes se describe cómo cambiar la apariencia del diagrama para que sea más fácil de leer.

## <a name="copying-elements"></a>Copiar elementos
 Puede copiar, cortar y pegar elementos en el diagrama de la definición de DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Acercar o alejar en el diagrama
 Puede acercar o alejar el diagrama mediante la barra Diseñador DSL **herramientas** para establecer el nivel de zoom.

## <a name="hiding-map-lines"></a>Ocultar líneas de asignación
 Las líneas de asignación son las líneas que se dibujan entre una clase dominio o una relación de dominio y la forma o conector al que se asigna. Puede ocultar las líneas de mapa haciendo clic en el **botón Mostrar líneas de** mapa de la barra **Diseñador DSL** herramientas. Para mostrar las líneas, vuelva a hacer clic en el botón.

## <a name="changing-the-diagram-layout"></a>Cambiar el diseño del diagrama
 Puede cambiar el diseño de la partición **Clases y relaciones** como se muestra a continuación.

### <a name="expandcollapse"></a>Expand/Collapse (Expandir o contraer)
 Puede reducir el tamaño de un elemento de forma de compartimiento que representa una clase de dominio o una forma haciendo clic con el botón derecho en él y, a continuación, haciendo clic **en Contraer**. Esto oculta el compartimiento **Propiedades del** dominio de la forma. Para volver a mostrar **el compartimiento Propiedades del** dominio, haga clic con el botón derecho en la forma y, a continuación, haga clic en **Expandir.**

### <a name="move-updown"></a>Move Up/Down (Subir o bajar)
 Puede mover una clase de dominio o un elemento de diagrama hacia  arriba o hacia abajo en la partición haciendo clic con el botón derecho en el elemento y, a continuación, haciendo clic en Subir **o Bajar.** Si mueve un elemento de marcador de posición que se muestra como el destino de una referencia de incrustación o referencia, la relación se moverá con él.

### <a name="expandcollapse-relationships-tree"></a>Expand/Collapse Relationships Tree (Expandir o contraer el árbol de relaciones)
 Si una clase de dominio desempeña el rol de origen en la inserción o las relaciones de referencia con otras clases de dominio, puede ocultar las relaciones haciendo clic con el botón derecho en la definición de clase de dominio y, a continuación, haciendo clic en Contraer árbol de **relaciones**. Para mostrar las relaciones, haga clic con el botón derecho en el elemento de definición y, a continuación, haga clic **en Expandir árbol de relaciones**.

### <a name="expandcollapse-inheritance-tree"></a>Expand/Collapse Inheritance Tree (Expandir o contraer el árbol de herencia)
 Si una clase de dominio es la clase base de otras clases de dominio, puede ocultar el árbol de herencia haciendo clic con el botón derecho en la definición de clase de dominio y, a continuación, haciendo clic **en Contraer árbol de herencia**. Para mostrar el árbol de herencia, haga clic con el botón derecho en el elemento de definición y, a continuación, haga clic **en Expandir árbol de herencia**.

### <a name="bring-tree-here"></a>Bring Tree Here
 Para consolidar el diagrama, haga clic con el botón derecho en una clase de dominio de marcador de posición y, a continuación, haga clic **en Bring Tree Here (Traer árbol aquí).** La clase de dominio de marcador de posición se convierte en un elemento de definición y muestra los árboles de herencia y de relaciones. El elemento de definición anterior se convierte en un elemento de marcador de posición si es el destino de una relación o el elemento secundario en una relación de herencia; de lo contrario, desaparece.

### <a name="split-tree"></a>Split Tree (Dividir árbol)
 Puede dividir los árboles de herencia o relaciones haciendo clic con el botón derecho en la definición de clase de dominio que los muestra y, a continuación, haciendo clic **en Dividir árbol**. El elemento de definición se convierte en un elemento de marcador de posición, y la clase de dominio de definición, junto con sus árboles de herencia y de relaciones, se muestran ahora en la parte inferior de la partición.

### <a name="show-as-class"></a>Show As Class
 Si una relación de dominio tiene relaciones derivadas o si tiene relaciones de inserción o referencia con otras relaciones de dominio, puede mostrar la relación como una clase haciendo clic con el botón derecho en la relación y, a continuación, haciendo clic en Mostrar como **clase**. La relación se mostrará con un compartimiento **Propiedades del** dominio y mostrará los árboles de herencia y relaciones.

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))