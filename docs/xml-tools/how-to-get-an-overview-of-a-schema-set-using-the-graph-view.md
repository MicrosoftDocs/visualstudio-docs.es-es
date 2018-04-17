---
title: 'Cómo: obtener una visión general de un conjunto de esquemas mediante la vista Gráfico | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 145a55312d042811b0d51d46136078657d10fee1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Cómo: Obtener información general de un conjunto de esquemas mediante la vista Gráfico
Este tema describe cómo utilizar el [vista gráfico](../xml-tools/graph-view.md) para obtener una vista general de los nodos de un conjunto de esquemas y las relaciones entre los nodos.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido  
  
1.  Cree un nuevo archivo de esquema XML y guarde el archivo como Relationships.xsd.  
  
2.  Haga clic en el **Use el Editor XML para ver y editar el archivo de esquema XML subyacente** vínculo en la vista inicio.  
  
3.  Copie el código de ejemplo de esquema XML del [esquema XML de ejemplo: relaciones](../xml-tools/sample-xsd-file-relationships.md) y péguelo para reemplazar el código que se ha agregado el nuevo archivo XSD de forma predeterminada.  
  
4.  Haga clic en cualquier lugar en el Editor XML y seleccione **Diseñador de vistas**.  
  
5.  Seleccione el vista Gráfico en la barra de herramientas XSD.  
  
6.  Seleccione **del conjunto de esquemas** nodo en el Explorador de esquemas XML y arrastre el nodo a la superficie de diseño de la vista gráfico. Debería ver todos los nodos globales y las flechas que conectan los nodos que tienen relaciones.  
  
     ![Vista gráfica](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Haga clic en cualquier nodo de la superficie de diseño y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.  
  
8.  Haga clic en cualquier nodo de elemento en la superficie de diseño y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.