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
ms.openlocfilehash: 9109b94f66a440b91e136266df6a8f896a01edcd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Cómo: Para pasar de las vistas al Editor XML

En este tema se muestra cómo pasar de las vistas del Diseñador de esquemas XML (Diseñador XSD) al Editor XML. Este ejemplo se utiliza la [esquema de pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Para pasar de las vistas al Editor XML

1.  Para crear y editar un nuevo archivo de esquema XML, siga los pasos de [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Para cambiar al diseñador de esquemas XML desde el Editor XML, haga clic en cualquier lugar en el Editor XML y seleccione **Diseñador de vistas**.

3.  Para cambiar a la vista de gráfico con la marca de agua, haga clic en el **usar la vista gráfico para ver la relación entre los nodos** vínculo en la vista inicio.

4.  Arrastre el nodo `USAddress` desde el Explorador de esquemas XML hasta la vista Gráfico. Haga clic en el `USAddress` nodo en la vista gráfico y seleccione **mostrar en vista de modelo de contenido** en el menú contextual.

     Aparece la vista Modelo de contenido con los detalles del nodo `USAddress`.

5.  Para cambiar a la vista Inicio desde la vista Modelo de contenido utilizando la barra de herramientas, haga clic en el botón de la vista Inicio en la barra de herramientas XSD.

6.  Para pasar de una vista a otra utilizando las teclas de acceso rápido, presione CTRL+1 para la vista Inicio, CTRL+2 para la vista Gráfico, y CTRL+3 para la vista Modelo de contenido.

7.  Para ir al Editor XML desde la vista de modelo de contenido, haga clic en el nodo y seleccione **ver código** en el menú contextual.