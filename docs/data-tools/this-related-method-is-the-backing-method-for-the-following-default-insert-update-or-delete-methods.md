---
title: "Este m&#233;todo relacionado es el m&#233;todo de copia de seguridad para los siguientes m&#233;todos de inserci&#243;n, actualizaci&#243;n o eliminaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Este m&#233;todo relacionado es el m&#233;todo de copia de seguridad para los siguientes m&#233;todos de inserci&#243;n, actualizaci&#243;n o eliminaci&#243;n
Este método relacionado es el método de copia de seguridad para los siguientes métodos de inserción, actualización o eliminación.Si se elimina, estos métodos se eliminarán también.¿Desea continuar?  
  
 El método seleccionado de `DataContext` se usa actualmente como uno de los métodos de inserción, actualización o eliminación para una de las clases de entidad en Object Relational Designer.Al eliminar el método seleccionado, la clase de entidad que usaba este método se revertirá al comportamiento predeterminado en tiempo de ejecución para realizar la inserción, actualización o eliminación durante una actualización.  
  
### Para eliminar el método seleccionado de modo que la clase de entidad utilizará las actualizaciones en tiempo de ejecución  
  
-   Haga clic en **Sí**.  
  
     El método seleccionado se elimina y las clases que usaban este método para invalidar el comportamiento de actualización se revierten al comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL.  
  
### Para cerrar el cuadro de mensaje sin cambiar el método seleccionado  
  
-   Haga clic en **No**.  
  
     El cuadro de mensaje se cierra y no se realiza ninguna modificación.  
  
## Vea también  
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)