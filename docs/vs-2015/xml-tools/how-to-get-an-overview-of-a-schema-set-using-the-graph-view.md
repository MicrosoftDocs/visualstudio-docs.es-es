---
title: 'Cómo: obtener información general de un conjunto de esquemas mediante la vista gráfico | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670896"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Cómo: Obtener información general de un conjunto de esquemas mediante la vista Gráfico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe cómo utilizar la [vista Gráfico](../xml-tools/graph-view.md) para obtener una vista general de los nodos en un conjunto de esquemas y de las relaciones entre los nodos.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido

1. Cree un nuevo archivo de esquema XML y guarde el archivo como Relationships.xsd.

2. Haga clic en el vínculo **usar el editor XML para ver y editar el archivo de esquema XML subyacente** en la vista Inicio.

3. Copie el código de ejemplo del esquema XML del [esquema XML de ejemplo: Relationships](../xml-tools/sample-xsd-file-relationships.md) y péguelo para reemplazar el código que se agregó al nuevo archivo XSD de forma predeterminada.

4. Haga clic con el botón secundario en cualquier parte del editor XML y seleccione **Diseñador de vistas**.

5. Seleccione el vista Gráfico en la barra de herramientas XSD.

6. Seleccione el nodo **conjunto de esquemas** en el explorador de esquemas XML y arrastre el nodo al superficie de diseño de la vista gráfico. Debería ver todos los nodos globales y las flechas que conectan los nodos que tienen relaciones.

     ![Vista de gráfico](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. Haga clic en cualquier nodo de la superficie de diseño y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.

8. Rick: haga clic en cualquier nodo de elemento en la superficie de la que se encuentra y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.
