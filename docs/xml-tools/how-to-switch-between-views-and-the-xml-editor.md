---
title: 'Cómo: Para pasar de las vistas al Editor XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b0eb90f2ead313ce94d609d71385b595f3e964b
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
ms.locfileid: "34477735"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Cómo: cambiar entre las vistas y el Editor XML

En este tema se muestra cómo pasar de las vistas del Diseñador de esquemas XML (Diseñador XSD) al Editor XML. Este ejemplo se utiliza la [esquema de pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Para pasar de las vistas al Editor XML

1.  Para crear y editar un nuevo archivo de esquema XML, siga los pasos de [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Para cambiar al diseñador de esquemas XML desde el Editor XML, haga clic en cualquier lugar en el Editor XML y seleccione **Diseñador de vistas**.

3.  Para cambiar a la vista de gráfico con la marca de agua, haga clic en el **usar la vista gráfico para ver la relación entre los nodos** vínculo en la vista inicio.

4.  Arrastre el `USAddress` nodo desde el **Explorador de esquemas XML** en la vista gráfico. Haga clic en el `USAddress` nodo en la vista gráfico y seleccione **mostrar en vista de modelo de contenido** en el menú contextual.

     Aparece la vista Modelo de contenido con los detalles del nodo `USAddress`.

5.  Para cambiar a la vista inicio desde la vista de modelo de contenido mediante la barra de herramientas, haga clic en el **vista inicio** botón en la barra de herramientas XSD.

6.  Para cambiar entre las vistas, usando las teclas de aceleración, presione **Ctrl**+**1** para la vista inicio, **Ctrl**+**2** para la vista de gráfico, y **Ctrl**+**3** para la vista de modelo de contenido.

7.  Para ir al Editor XML desde la vista de modelo de contenido, haga clic en el nodo y seleccione **ver código** en el menú contextual.