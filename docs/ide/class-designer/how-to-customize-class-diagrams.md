---
title: 'Cómo: Personalizar los diagramas de clases (Diseñador de clases)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 129f1453b32052fb50a049f413d05bf562e6d4b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Cómo: Personalizar diagramas de clases (Diseñador de clases)

Es posible cambiar la manera en que se muestra la información en los diagramas de clases. Se puede personalizar el diagrama entero o los tipos individuales en la superficie de diseño.

Por ejemplo, se puede ajustar el nivel de zoom de un diagrama de clase completo, cambiar cómo se agrupan y ordenan determinados miembros de tipo, ocultar o mostrar relaciones, así como mover conjuntos de tipos o tipos individuales en cualquier parte del diagrama.

> [!NOTE]
> Personalizar la manera en que las formas aparecen en el diagrama no cambia el código subyacente para los tipos representados en el diagrama.

Las secciones que contienen miembros de tipo, como la sección **Propiedades** de una clase, se denominan compartimientos. Puede ocultar o mostrar los compartimientos y los miembros de tipo individualmente.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Acercar y alejar el diagrama de clase

1.  Abra y seleccione un archivo de diagrama de clases en **Diseñador de clases**.

2.  En la barra de herramientas **Diseñador de clases**, haga clic en el botón **Acercar** o **Alejar** para cambiar el nivel de zoom de la superficie del diseñador.

     o

     Especifique un valor de zoom determinado. Puede usar la lista desplegable **Zoom** o escribir un nivel de zoom válido (el intervalo válido está comprendido entre el 10 % y el 400 %).

    > [!NOTE]
    > Al cambiar el nivel de zoom, no se ve afectada la escala de la copia impresa del diagrama de clases.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Personalizar la agrupación y ordenación de los miembros de tipo

1.  Abra y seleccione un archivo de diagrama de clases en **Diseñador de clases**.

2.  Haga clic con el botón secundario en un área vacía de la superficie de diseño y elija **Miembros del grupo**.

3.  Seleccione una de las opciones disponibles:

    1.  **Agrupar por tipo** separa los miembros de tipo individuales en una lista agrupada de Propiedades, Métodos, Eventos y Campos. Cada grupo depende de la definición de las entidades: por ejemplo, una clase no mostrará ningún grupo de eventos si todavía no hay ningún evento definido para esa clase.

    2.  **Agrupar por acceso** separa los miembros de tipo individuales en una lista agrupada según los modificadores de acceso del miembro. Por ejemplo, Público y Privado.

    3.  **Ordenar alfabéticamente** muestra los elementos que constituyen una entidad como una única lista ordenada alfabéticamente. La lista se ordena de menor a mayor.

## <a name="hide-compartments-on-a-type"></a>Ocultar los compartimientos de un tipo

1.  Abra y seleccione un archivo de diagrama de clases en **Diseñador de clases**.

2.  Haga clic con el botón secundario en la categoría de miembro del tipo que desea personalizar (por ejemplo, seleccione el nodo **Métodos** de una clase.

3.  Haga clic en **Ocultar compartimiento**.

     El compartimiento seleccionado desaparece del contenedor del tipo.

## <a name="hide-individual-members-on-a-type"></a>Ocultar miembros individuales de un tipo

1.  Abra y seleccione un archivo de diagrama de clases en **Diseñador de clases**.

2.  Haga clic con el botón secundario en el miembro del tipo que desea ocultar.

3.  Haga clic en **Ocultar**.

     El miembro seleccionado desaparece del contenedor del tipo.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Mostrar los compartimientos y miembros ocultos de un tipo

1.  Abra y seleccione un archivo de diagrama de clases en **Diseñador de clases**.

2.  Haga clic con el botón secundario en el nombre del tipo con el compartimiento oculto.

3.  Haga clic en **Mostrar todos los miembros**.

     Todos los compartimientos y miembros ocultos aparecen en el contenedor del tipo.

## <a name="hide-relationships"></a>Ocultar relaciones

1.  Abra y seleccione un archivo de diagrama de clases en **Diseñador de clases**.

2.  Haga clic con el botón secundario en la línea de asociación o herencia que desea ocultar.

3.  Haga clic en **Ocultar** para las líneas de asociación y en **Ocultar línea de herencia** para las líneas de herencia.

4.  Haga clic en **Mostrar todos los miembros**.

     Todos los compartimientos y miembros ocultos aparecen en el contenedor del tipo.

## <a name="show-hidden-relationships"></a>Mostrar relaciones ocultas

1.  Abra y seleccione un archivo de diagrama de clases en **Diseñador de clases**.

2.  Haga clic con el botón secundario en el tipo con la asociación o herencia oculta.

 Haga clic en **Mostrar todos los miembros** para las líneas de asociación y en **Mostrar clase base** o **Mostrar clases derivadas** para las líneas de herencia.

## <a name="remove-a-shape-from-a-class-diagram"></a>Quitar una forma de un diagrama de clase
Se puede quitar una forma de tipo del diagrama de clase sin que ello afecte al código subyacente del tipo. Al quitar las formas de tipo de un diagrama de clases solo se ve afectado ese diagrama: no se ve afectado el código subyacente que define el tipo y otros diagramas que muestran el tipo.

1.  En el diagrama de clases, seleccione la forma de tipo que desee quitar del diagrama.

2.  En el menú **Edición**, elija **Quitar del diagrama**.

     La forma de tipo y cualquier línea de asociación o herencia conectada a ella dejan de aparecer en el diagrama.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Eliminar una forma de tipo y su código subyacente

1.  Haga clic con el botón secundario del mouse en la forma, en la superficie de diseño.

2.  Seleccione **Eliminar código** en el menú contextual.

     La forma se quita del diagrama y su código subyacente se elimina del proyecto.

## <a name="see-also"></a>Vea también

- [Trabajar con diagramas de clases](working-with-class-diagrams.md)
- [Cómo: Cambiar entre notación de miembro y notación de asociación](how-to-change-between-member-notation-and-association-notation.md)
- [Cómo: Ver los tipos existentes](how-to-view-existing-types.md)
- [Visualización de tipos y relaciones](viewing-types-and-relationships.md)