---
title: "Extensión de Excel de muestra: ActionFilter (Clase) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 8f2aa063163898a87ff563a356f6bb389cb07243
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensión de Excel de muestra: ActionFilter (Clase)
Esta clase interna extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> y representa un filtro para las acciones de prueba en un elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## <a name="simple-properties"></a>Propiedades simples  
 Estas propiedades de solo lectura permiten al programador especificar cómo el marco de pruebas de IU codificadas va a ejecutar este filtro de acción de prueba. Por ejemplo, la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> proporciona el nombre del filtro de acción. Otras propiedades obtienen <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> del filtro de acción, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A> y el nombre <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> para las acciones de prueba que se filtran mediante este filtro de acción de prueba. Otras indican si <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> y también si la acción de prueba es <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>Método ProcessRule  
 Este método se llama mediante el marco de prueba de IU codificada y ejecuta el filtro en el <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> proporcionado. Esta invalidación determinada quita una acción de elección de mouse en una celda cuando la siguiente acción en la pila envía pulsaciones de tecla a la celda. Después, devuelve `false`.  
  
## <a name="private-methods"></a>Métodos privados  
 El método `IsLeftClick` determina si la acción proporcionada representa un clic del mouse. El método `AreActionsOnSameExcelCell` determina si dos acciones proporcionadas que se ejecutan en la misma celda en Excel.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
