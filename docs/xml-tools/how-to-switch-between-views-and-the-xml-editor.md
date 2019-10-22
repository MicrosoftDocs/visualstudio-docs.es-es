---
title: 'Cómo: cambiar entre las vistas y el editor XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f8049806d14abc8e22154a763e982ce5c86304b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601879"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Cómo: cambiar entre las vistas y el editor XML

En este tema se muestra cómo cambiar entre las vistas del diseñador de esquemas XML (diseñador XSD) y el editor XML. En este ejemplo se utiliza el [esquema del pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Para cambiar entre las vistas y el editor XML

1. Para crear y editar un nuevo archivo de esquema XML, siga los pasos descritos en [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Para cambiar al diseñador de esquemas XML desde el editor XML, haga clic con el botón secundario en cualquier parte del editor XML y seleccione **Diseñador de vistas**.

3. Para cambiar a la vista Gráfico con la marca de agua, haga clic en la **vista usar el gráfico para ver la relación entre el** vínculo de los nodos de la vista Inicio.

4. Arrastre el nodo `USAddress` desde el **Explorador de esquemas XML** hasta la vista gráfico. Haga clic con el botón secundario en el nodo `USAddress` de la vista gráfico y seleccione **Mostrar en la vista modelo de contenido** en el menú contextual.

     Aparece la vista Modelo de contenido con los detalles del nodo `USAddress`.

5. Para cambiar a la vista inicio desde la vista modelo de contenido mediante la barra de herramientas, haga clic en el botón **iniciar vista** de la barra de herramientas xsd.

6. Para alternar entre las vistas mediante las teclas de inicio de teclas, presione **ctrl** +**1** para la vista Inicio, **Ctrl** +**2** para la vista gráfico y **Ctrl** +**3** para la vista modelo de contenido.

7. Para ir al editor XML desde la vista modelo de contenido, haga clic con el botón secundario en el nodo y seleccione **Ver código** en el menú contextual.