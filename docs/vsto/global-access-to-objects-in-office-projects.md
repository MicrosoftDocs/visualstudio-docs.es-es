---
title: Acceso global a objetos en los proyectos de Office | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fda3dee12cdea7442d0f92a2ba794551d76b14cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="global-access-to-objects-in-office-projects"></a>Acceso global a objetos en los proyectos de Office
  Cuando se crea un proyecto de Office, Visual Studio genera automáticamente una clase denominada `Globals` en el proyecto. Puede utilizar la clase `Globals` para tener acceso en tiempo de ejecución a diversos elementos del proyecto desde cualquier código del proyecto.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Cómo utilizar la clase Globals  
 `Globals` es una clase estática que mantiene referencias a determinados elementos del proyecto. Mediante el uso de la clase `Globals` puede tener acceso a los siguientes elementos desde cualquier código del proyecto en tiempo de ejecución:  
  
-   Las clases `ThisWorkbook` y `Sheet`*n* de un proyecto de libro o plantilla de Excel. Puede tener acceso a estos objetos mediante las propiedades `Globals.ThisWorkbook` y `Sheet`*n* .  
  
-   La clase `ThisDocument` de un proyecto de documento o plantilla de Word. Puede tener acceso a este objeto mediante la propiedad `Globals.ThisDocument` .  
  
-   La clase `ThisAddIn` en un proyecto de complemento de VSTO. Puede tener acceso a este objeto mediante la propiedad `Globals.ThisAddIn` .  
  
-   Todas las cintas de opciones del proyecto que haya personalizado mediante el Diseñador de la cinta de opciones. Puede tener acceso a las cintas de opciones mediante la propiedad `Globals.Ribbons` . Para obtener más información, consulta [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md).  
  
-   Todas las áreas de formulario de Outlook en un proyecto de complemento de VSTO para Outlook. Puede tener acceso a las áreas de formulario mediante la propiedad `Globals.FormRegions` . Para obtener más información, consulta [Accessing a Form Region at Run Time](../vsto/accessing-a-form-region-at-run-time.md).  
  
-   Un objeto generador que permite crear controles de cinta y hospedar elementos en tiempo de ejecución en los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Puede tener acceso a este objeto mediante la propiedad `Globals.Factory` . Este objeto es una instancia de una clase que implementa una de las interfaces siguientes:  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 Por ejemplo, puede utilizar la propiedad `Globals.Sheet1` para insertar texto en un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en `Sheet1` , cuando un usuario haga clic en un botón del panel de acciones en un proyecto de nivel de documento para Excel.  
  
 [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
 [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initializing-the-globals-class"></a>Inicializar la clase Globals  
 El código que intente usar la clase `Globals` antes de que se inicialice completamente el documento o el complemento de VSTO, podría producir una excepción de tiempo de ejecución. Por ejemplo, el uso de `Globals` al declarar una variable de nivel de clase podría provocar un error, ya que la clase `Globals` podría no estar inicializada con referencias a todos los elementos host antes de que se creara una instancia del objeto declarado.  
  
> [!NOTE]  
>  La clase `Globals` nunca se inicializa en tiempo de diseño, sino que el diseñador crea instancias de controles. Esto significa que si crea un control de usuario que utiliza una propiedad de la clase `Globals` desde dentro de una clase de control de usuario, deberá comprobar si la propiedad devuelve **null** antes de intentar usar el objeto devuelto.  
  
## <a name="see-also"></a>Vea también  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento Host Document](../vsto/document-host-item.md)   
 [Elemento Host Workbook](../vsto/workbook-host-item.md)   
 [Elemento Host Worksheet](../vsto/worksheet-host-item.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  