---
title: 'Cómo: cambiar entre las vistas y el editor XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54e43b00c877f5453d1dc28bbc9d5546fcef056f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592637"
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

6. Para alternar entre las vistas mediante las teclas de inicio de teclas, presione **ctrl**+**1** para la vista Inicio, **Ctrl**+**2** para la vista gráfico y **Ctrl**+**3** para la vista modelo de contenido.

7. Para ir al editor XML desde la vista modelo de contenido, haga clic con el botón secundario en el nodo y seleccione **Ver código** en el menú contextual.
