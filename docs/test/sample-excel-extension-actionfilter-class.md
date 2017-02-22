---
title: "Extensi&#243;n de Excel de muestra: ActionFilter (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Extensi&#243;n de Excel de muestra: ActionFilter (Clase)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta clase interna extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> y representa un filtro para las acciones de pruebas en un elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Propiedades simples  
 Estas propiedades de solo lectura permiten al desarrollador especificar cómo ejecutará el marco de pruebas de IU codificadas este filtro de acción de pruebas.  Por ejemplo, la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> proporciona el nombre del filtro de acción.  Otras propiedades obtienen la <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> del filtro de acción, el <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, el nombre <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> para las acciones de pruebas filtradas por este filtro de acción de pruebas.  Otras indican si se aplica tiempo de espera \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>\) y también si la acción de prueba está habilitada \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>\).  
  
## Método ProcessRule  
 El marco de pruebas de IU codificadas llama a este método y ejecuta el filtro en la pila <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> proporcionada.  Esta invalidación concreta quita una acción de elección del mouse en una celda cuando la siguiente acción de la pila envía pulsaciones a la celda.  Después, devuelve `false`.  
  
## Métodos privados  
 El método `IsLeftClick` determina si la acción proporcionada representa un clic con el botón primario del mouse.  El método `AreActionsOnSameExcelCell` determina si se ejecutan dos acciones proporcionadas en la misma celda en Excel.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)