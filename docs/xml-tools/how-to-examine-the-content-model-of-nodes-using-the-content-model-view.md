---
title: "C&#243;mo: Examinar el Modelo de contenido de los nodos mediante la vista de Modelo de contenido | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# C&#243;mo: Examinar el Modelo de contenido de los nodos mediante la vista de Modelo de contenido
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo explorar los nodos mediante [Vista Modelo de contenido](../xml-tools/content-model-view.md).  
  
### Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido  
  
1.  Cree un nuevo archivo de esquema XML.  
  
2.  Haga clic en **Use el Editor XML para ver y editar el archivo de esquema XML subyacente** en la vista Inicio.  
  
3.  Copie el código de ejemplo del Esquema XML desde el [Esquema XML de muestra: Esquema de pedido de compra](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md) y péguelo para reemplazar el código que se agregó de forma predeterminada al nuevo archivo XSD.  
  
4.  Seleccione el elemento `purchaseOrder` en el Explorador de esquemas haciendo clic con el botón secundario del mouse en el elemento `purchaseOrder` en el Editor XML y seleccionando **Mostrar en el Explorador de esquemas XML**.  
  
5.  Haga clic con el botón secundario en `purchaseOrder` dentro del Explorador XML y seleccione **Mostrar en la vista Modelo de contenido**.  
  
     La vista Modelo de contenido muestra el elemento `purchaseOrder` en la superficie de diseño.  
  
6.  Expanda los nodos `shipTo`, `items` y `billTo` haciendo doble clic en cada nodo o haciendo clic en la flecha doble situada a la derecha de cada nodo.  
  
     Los nodos del elemento `purchaseOrder` se expanden y puede ver el modelo de contenido del elemento.  
  
7.  Haga clic en cualquier nodo situado debajo del elemento `purchaseOrder` y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.  
  
8.  Haga clic en el botón **Mostrar documentación** en la barra de herramientas XSD para ver la documentación.También puede hacer clic con el botón secundario en la superficie de diseño para ver la documentación.  
  
9. Haga clic con el botón secundario en el nodo `purchaseOrder` y seleccione **Generar XML de muestra** para ver el documento de instancia XML.