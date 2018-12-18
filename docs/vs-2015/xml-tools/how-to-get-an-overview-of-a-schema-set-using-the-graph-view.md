---
title: 'Cómo: obtener una visión general de un conjunto de esquemas mediante la vista Gráfico | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3722af4aef2f56d6da1c2a79840c05edd2a87b65
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181368"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Cómo: Obtener información general de un conjunto de esquemas mediante la vista Gráfico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Este tema describe cómo usar el [vista gráfico](../xml-tools/graph-view.md) para ver una visión general de los nodos de un conjunto de esquemas y las relaciones entre los nodos.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido  
  
1.  Cree un nuevo archivo de esquema XML y guarde el archivo como Relationships.xsd.  
  
2.  Haga clic en el **Use el Editor XML para ver y editar el archivo de esquema XML subyacente** vínculo en la vista inicio.  
  
3.  Copie el código de ejemplo de esquema XML de [esquema XML de muestra: relaciones](../xml-tools/sample-xsd-file-relationships.md) y péguelo para reemplazar el código que se ha agregado el nuevo archivo XSD de forma predeterminada.  
  
4.  Haga clic en cualquier lugar en el Editor XML y seleccione **Diseñador de vistas**.  
  
5.  Seleccione el vista Gráfico en la barra de herramientas XSD.  
  
6.  Seleccione **del conjunto de esquemas** nodo en el Explorador de esquemas XML y arrastre el nodo a la superficie de diseño de la vista gráfico. Debería ver todos los nodos globales y las flechas que conectan los nodos que tienen relaciones.  
  
     ![Vista gráfica](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Haga clic en cualquier nodo de la superficie de diseño y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.  
  
8.  Haga clic en cualquier nodo de elemento de la con superficie y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.



