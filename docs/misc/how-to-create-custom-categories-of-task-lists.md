---
title: "C&#243;mo: crear categor&#237;as personalizadas de listas de tareas | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lista de tareas, categorías personalizadas"
ms.assetid: 5e4ac1b1-9afb-46c5-9dcc-6cab9c5ceee8
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# C&#243;mo: crear categor&#237;as personalizadas de listas de tareas
Las categorías personalizadas de tareas proporcionan el control sobre las tareas se muestran en la ventana de **Lista de tareas** .  
  
 implemente una categoría personalizada de tareas por las razones siguientes:  
  
-   Desea controlar dónde las categorías se muestran \(ordenado\) en la lista de categorías.  
  
-   Tiene varias subcategorías de tareas que desea ordenar en una categoría sin otras tareas que ordena entre ellas.  
  
-   Desea crear una vista personalizada en la que solo se muestren las tareas.  
  
    > [!NOTE]
    >  Puede lograr efectos similares a las categorías personalizadas realmente implementar una categoría personalizada.  Por ejemplo, puede mostrar un mapa de bits para una categoría o subcategoría implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2.ImageList%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.ImageListIndex%2A>.  Las fuentes del proveedor de la tarea la lista y después cada tarea proporciona un índice en la lista.  
  
 Para crear una categoría personalizada en **Lista de tareas**, regístrelo con **Lista de tareas** mediante el procedimiento siguiente.  
  
### Para registrar una categoría de la lista de tareas personalizado  
  
-   Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterCustomCategory%2A> para registrar una categoría personalizada con la lista de tareas.  
  
     cada categoría personalizada debe tener su propio GUID, que se especifica en el parámetro de `guidCat` .  En el parámetro de `dwSortOrder` , especifique la ubicación donde desea que esta categoría clasificara \(cuando la lista está ordenada por categorías\).  Este método se devuelve la posición real de ordenación categoría personalizada dentro de la lista mayor de categorías.  
  
     Los criterios de ordenación para las categorías de tareas integradas, que están definidos en la enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKCATEGORY> , están en la tabla siguiente.  
  
    |Categoría|Valor|Descripción|  
    |---------------|-----------|-----------------|  
    |CAT\_ALL|1|no una categoría real.  Utilizado para permitir que una vista de lista de tareas muestra todas las tareas en **Lista de tareas**.|  
    |CAT\_BUILDCOMPILE|10|Errores de compilación, advertencias y, posiblemente errores de implementación.|  
    |CAT\_COMMENTS|20|Tareas generadas por comentarios especiales, como “TODO,” UNDONE,” o “HACK.”|  
    |CAT\_CODESENSE|30|Los errores generados mientras escribe código fuente.|  
    |CAT\_SHORTCUTS|40|Accesos directos al código.|  
    |CAT\_USER|50|Tareas realizadas por el usuario.|  
    |CAT\_MISC|60|Tareas diferentes que VSPackages posible desee agregar a **Lista de tareas**.|  
    |CAT\_HTML|70|Tareas que pertenecen al desarrollo de páginas Web.|  
  
     Por ejemplo, para incluir una categoría entre CAT\_CODESENSE y CAT\_SHORTCUTS, es posible que pase un valor de 31 para el criterio de ordenación.  Sin embargo, dado que un valor de 31 se puede utilizar ya por otro proveedor de la categoría de la tarea personalizada, **Lista de tareas** se le asigna la categoría de tareas para la entrada vacía siguiente.  Este valor se pasa de nuevo en el parámetro de `pCat` .  
  
### Anular el registro de una categoría de la lista de tareas personalizado  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.UnregisterCustomCategory%2A> de llamada para anular el registro de la categoría personalizada.  
  
## Vea también  
 [Creación de vistas de lista de tareas personalizadas](../misc/creating-custom-task-list-views.md)