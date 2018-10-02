---
title: 'Extensión de Excel de muestra: ActionFilter (Clase) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5e6aff4a57dfb84760ceb4513e06d063c01a5af0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578623"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensión de Excel de muestra: ActionFilter (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [extensión de Excel: clase ActionFilter](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-actionfilter-class).  
  
Esta clase interna extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> y representa un filtro para las acciones de prueba en un elemento [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
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



