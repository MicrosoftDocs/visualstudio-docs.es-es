---
title: "Extensión de Excel de muestra: ActionFilter (Clase) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.openlocfilehash: 346cb9faddf2bd155c91d9fc72176020ba43197b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
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
