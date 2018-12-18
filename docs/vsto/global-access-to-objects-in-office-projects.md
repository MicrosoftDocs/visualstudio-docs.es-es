---
title: Acceso global a objetos en los proyectos de Office
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
ms.openlocfilehash: 018ffc5c165c8cea7df66911c71f636712df4229
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932046"
---
# <a name="global-access-to-objects-in-office-projects"></a>Acceso global a objetos en los proyectos de Office
  Cuando se crea un proyecto de Office, Visual Studio genera automáticamente una clase denominada `Globals` en el proyecto. Puede utilizar la clase `Globals` para tener acceso en tiempo de ejecución a diversos elementos del proyecto desde cualquier código del proyecto.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Cómo usar la clase Globals  
 `Globals` es una clase estática que mantiene referencias a determinados elementos del proyecto. Mediante el uso de la clase `Globals` puede tener acceso a los siguientes elementos desde cualquier código del proyecto en tiempo de ejecución:  
  
- Las clases `ThisWorkbook` y `Sheet`*n* de un proyecto de libro o plantilla de Excel. Puede tener acceso a estos objetos mediante las propiedades `Globals.ThisWorkbook` y `Sheet`*n* .  
  
- La clase `ThisDocument` de un proyecto de documento o plantilla de Word. Puede tener acceso a este objeto mediante la propiedad `Globals.ThisDocument` .  
  
- La `ThisAddIn` clase en un proyecto de complemento VSTO. Puede tener acceso a este objeto mediante la propiedad `Globals.ThisAddIn` .  
  
- Todas las cintas de opciones del proyecto que haya personalizado mediante el Diseñador de la cinta de opciones. Puede tener acceso a las cintas de opciones mediante la propiedad `Globals.Ribbons` . Para obtener más información, consulte [tener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md).  
  
- Todas las áreas de formulario de Outlook en un proyecto de complemento de VSTO para Outlook. Puede tener acceso a las áreas de formulario mediante la propiedad `Globals.FormRegions` . Para obtener más información, consulte [tener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md).  
  
- Un objeto generador que permite crear controles de cinta y hospedar elementos en tiempo de ejecución en los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Puede tener acceso a este objeto mediante la propiedad `Globals.Factory` . Este objeto es una instancia de una clase que implementa una de las interfaces siguientes:  
  
  -   <xref:Microsoft.Office.Tools.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
  Por ejemplo, puede utilizar la propiedad `Globals.Sheet1` para insertar texto en un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en `Sheet1` , cuando un usuario haga clic en un botón del panel de acciones en un proyecto de nivel de documento para Excel.  
  
  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initialize-the-globals-class"></a>Inicializar la clase Globals  
 El código que intenta utilizar el `Globals` clase antes de inicializa el documento o el complemento de VSTO podría producir una excepción de tiempo de ejecución. Por ejemplo, el uso de `Globals` al declarar una variable de nivel de clase podría provocar un error, ya que la clase `Globals` podría no estar inicializada con referencias a todos los elementos host antes de que se creara una instancia del objeto declarado.  
  
> [!NOTE]  
>  La clase `Globals` nunca se inicializa en tiempo de diseño, sino que el diseñador crea instancias de controles. Esto significa que si crea un control de usuario que utiliza una propiedad de la clase `Globals` desde dentro de una clase de control de usuario, deberá comprobar si la propiedad devuelve **null** antes de intentar usar el objeto devuelto.  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento host Document](../vsto/document-host-item.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
  