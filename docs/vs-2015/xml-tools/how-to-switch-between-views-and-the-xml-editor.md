---
title: 'Cómo: cambiar entre las vistas y el editor XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28267f705dd9a747d0e3f3ac5dc2869ab7de8f6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656319"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Cómo: Para pasar de las vistas al Editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se muestra cómo pasar de las vistas del Diseñador de esquemas XML (Diseñador XSD) al Editor XML. En este ejemplo se utiliza el [esquema del pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md).

### <a name="to-switch-between-the-views-and-the-xml-editor"></a>Para pasar de las vistas al Editor XML

1. Para crear y editar un nuevo archivo de esquema XML, siga los pasos descritos en [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Para cambiar al diseñador de esquemas XML desde el editor XML, haga clic con el botón secundario en cualquier parte del editor XML y seleccione **Diseñador de vistas**.

3. Para pasar a la vista Gráfico utilizando la marca de agua, haga clic en el vínculo **Usar la vista Gráfico para ver las relaciones entre los nodos** en la vista Inicio.

4. Arrastre el nodo `USAddress` desde el Explorador de esquemas XML hasta la vista Gráfico. Haga clic con el botón derecho en el nodo `USAddress` en la vista Gráfico y seleccione **Mostrar en la vista Modelo de contenido** en el menú contextual.

     Aparece la vista Modelo de contenido con los detalles del nodo `USAddress`.

5. Para cambiar a la vista Inicio desde la vista Modelo de contenido utilizando la barra de herramientas, haga clic en el botón de la vista Inicio en la barra de herramientas XSD.

6. Para pasar de una vista a otra utilizando las teclas de acceso rápido, presione CTRL+1 para la vista Inicio, CTRL+2 para la vista Gráfico, y CTRL+3 para la vista Modelo de contenido.

7. Para ir al editor XML desde la vista modelo de contenido, haga clic con el botón secundario en el nodo y seleccione **Ver código** en el menú contextual.
