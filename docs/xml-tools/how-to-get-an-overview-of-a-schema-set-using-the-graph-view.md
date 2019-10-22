---
title: 'Diseñador de esquemas XML: obtener información general del conjunto de esquemas mediante la vista gráfico'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8acc2ff6a41f7057818c4a7659f2aa9d07c8bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651180"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Cómo: obtener información general de un conjunto de esquemas mediante la vista gráfico

En este tema se describe cómo usar la [vista de gráfico](../xml-tools/graph-view.md) para ver una vista de alto nivel de los nodos de un conjunto de esquemas y las relaciones entre los nodos.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido

1. Cree un nuevo archivo de esquema XML y guarde el archivo como *Relationships. xsd*.

2. Haga clic en el vínculo **usar el editor XML para ver y editar el archivo de esquema XML subyacente** en la vista Inicio.

3. Copie el código de ejemplo del esquema XML del [esquema XML de ejemplo: Relationships](../xml-tools/sample-xsd-file-relationships.md) y péguelo para reemplazar el código que se agregó al nuevo archivo XSD de forma predeterminada.

4. Haga clic con el botón secundario en cualquier parte del editor XML y seleccione **Diseñador de vistas**.

5. Seleccione la vista Gráfico en la **barra de herramientas XSD**.

6. Seleccione el nodo **conjunto de esquemas** en el **Explorador de esquemas XML** y arrastre el nodo a la superficie de diseño de la vista gráfico. Debería ver todos los nodos globales y las flechas que conectan los nodos que tienen relaciones.

     ![Vista de gráfico](../xml-tools/media/relationshipingraphview.gif)

7. Haga clic en cualquier nodo de la superficie de diseño y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.

8. Rick: haga clic en cualquier nodo de elemento en la superficie de diseño y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.