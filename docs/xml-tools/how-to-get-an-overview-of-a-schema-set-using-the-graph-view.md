---
title: Obtención de información general de un conjunto de esquemas
description: 'Diseñador de esquemas XML: Aprenda a usar la vista Gráfico del Diseñador de esquemas XML para obtener una vista general de los nodos de un conjunto de esquemas y de las relaciones entre los nodos.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 896522f6d7f057d359cb5502c42edf34d0a2d823
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897457"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>Procedimiento: Obtención de información general de un conjunto de esquemas con la vista Gráfico

En este tema se describe cómo utilizar la [vista Gráfico](../xml-tools/graph-view.md) para obtener una vista general de los nodos en un conjunto de esquemas y de las relaciones entre los nodos.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido

1. Cree un archivo de esquema XML y guárdelo como *Relationships.xsd*.

2. Haga clic en el vínculo **Use el Editor XML para ver y editar el archivo de esquema XML subyacente** en la vista Inicio.

3. Copie el código de ejemplo del Esquema XML desde [Esquema XML de ejemplo: relaciones](../xml-tools/sample-xsd-file-relationships.md) y péguelo para reemplazar el código que se agregó de forma predeterminada al nuevo archivo XSD.

4. Haga clic con el botón derecho en cualquier parte del Editor XML y seleccione **Diseñador de vistas**.

5. Seleccione la vista Gráfico en la **Barra de herramientas de XSD**.

6. Seleccione el nodo **Conjunto de esquemas** en el **Explorador de esquemas XML** y arrastre el nodo hasta la superficie de diseño de la vista Gráfico. Debería ver todos los nodos globales y las flechas que conectan los nodos que tienen relaciones.

     ![Vista de gráfico](../xml-tools/media/relationshipingraphview.gif)

7. Haga clic en cualquier nodo de la superficie de diseño y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.

8. Haga clic con el botón derecho en cualquier nodo del elemento de la superficie de diseño y seleccione **Generar XML de ejemplo** para ver el documento XML de instancia.
