---
title: Procedimiento Cambiar entre vistas y el editor XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35839f8ae33068333259b30015e4cae0bb9c26d3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110822"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Procedimiento Cambio entre las vistas y el editor XML

En este tema se muestra cómo cambiar entre las vistas del Diseñador de esquemas XML (diseñador XSD) y el editor XML. Este ejemplo se usa el [esquema de pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Para cambiar entre las vistas y el editor XML

1. Para crear y editar un nuevo archivo de esquema XML, siga los pasos de [Cómo: Crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Para cambiar al diseñador de esquemas XML desde el editor XML, haga clic en cualquier lugar en el editor XML y seleccione **Diseñador de vistas**.

3. Para cambiar a la vista gráfico utilizando la marca de agua, haga clic en el **usar la vista gráfico para ver la relación entre los nodos** vínculo en la vista inicio.

4. Arrastre el `USAddress` nodo desde el **Explorador de esquemas XML** hasta la vista gráfico. Haga clic en el `USAddress` nodo en la vista gráfico y seleccione **mostrar en vista de modelo de contenido** en el menú contextual.

     Aparece la vista Modelo de contenido con los detalles del nodo `USAddress`.

5. Para cambiar a la vista inicio desde la vista de modelo de contenido mediante la barra de herramientas, haga clic en el **vista inicio** en la barra de herramientas XSD.

6. Para cambiar entre las vistas, usando las teclas de aceleración, presione **Ctrl**+**1** para la vista inicio, **Ctrl**+**2** para la vista de gráfico, y **Ctrl**+**3** para la vista de modelo de contenido.

7. Para ir al editor XML desde la vista de modelo de contenido, haga clic en el nodo y seleccione **ver código** en el menú contextual.