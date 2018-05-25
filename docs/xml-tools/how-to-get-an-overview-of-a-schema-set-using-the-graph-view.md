---
title: 'Cómo: obtener una visión general de un conjunto de esquemas mediante la vista Gráfico de esquema XML del diseñador'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8be2666316bdc4d64d4f3dd4ec52c5104a1af5cc
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Cómo: obtener una visión general de un esquema configurado mediante la vista de gráfico

Este tema describe cómo utilizar el [vista gráfico](../xml-tools/graph-view.md) para obtener una vista general de los nodos de un conjunto de esquemas y las relaciones entre los nodos.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido

1.  Crear un nuevo archivo de esquema XML y guarde el archivo como *Relationships.xsd*.

2.  Haga clic en el **Use el Editor XML para ver y editar el archivo de esquema XML subyacente** vínculo en la vista inicio.

3.  Copie el código de ejemplo de esquema XML del [esquema XML de ejemplo: relaciones](../xml-tools/sample-xsd-file-relationships.md) y péguelo para reemplazar el código que se ha agregado el nuevo archivo XSD de forma predeterminada.

4.  Haga clic en cualquier lugar en el Editor XML y seleccione **Diseñador de vistas**.

5.  Seleccione la vista de gráfico en el **barra de herramientas XSD**.

6.  Seleccione **del conjunto de esquemas** nodo en el **Explorador de esquemas XML** y arrastre el nodo para la superficie de diseño de la vista gráfico. Debería ver todos los nodos globales y las flechas que conectan los nodos que tienen relaciones.

     ![Vista gráfica](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7.  Haga clic en cualquier nodo de la superficie de diseño y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.

8.  Haga clic en cualquier nodo de elemento en la superficie de diseño y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.