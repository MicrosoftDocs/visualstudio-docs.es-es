---
title: "Cambios en el diseño de proyectos de Office destinados a .NET Framework 4 o .NET Framework 4.5 | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 059d259b669e63c26759782010be7ff78691ffc3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Cambios en el diseño de proyectos de Office destinados a .NET Framework 4 o .NET Framework 4.5
  A partir de [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio introdujo algunos cambios en el diseño de los proyectos de Office destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Si está familiarizado con los proyectos de Office en versiones anteriores de Visual Studio, debe tener en cuenta estos cambios a la hora de desarrollar proyectos de Office destinados a esas versiones de .NET Framework 4.0 o versiones posteriores. De forma predeterminada, todos los proyectos creados con Visual Studio 2013 o versiones posteriores van destinados a .NET Framework 4.0 o versiones posteriores.  
  
 En las secciones siguientes se describen estos cambios de diseño de los proyectos de Office.  
  
## <a name="understanding-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Introducción al diseño basado en interfaces del Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office  
 Al desarrollar un proyecto de Office destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, la mayoría de los tipos que se usan en el Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office son interfaces. Este es un importante cambio con respecto a las versiones anteriores del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], donde estos tipos eran clases. Por ejemplo, cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos <xref:Microsoft.Office.Tools.Excel.Worksheet> y <xref:Microsoft.Office.Tools.Word.Document> son interfaces en lugar de clases. Para obtener más información, consulta [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 En los tipos cuya instancia se pudieron crear directamente en versiones anteriores de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], ahora se usan métodos del objeto Globals.Factory para obtener las instancias de estos tipos. Por ejemplo, para obtener un objeto que implementa el <xref:Microsoft.Office.Tools.Excel.SmartTag> la interfaz, use el método Globals.Factory.CreateSmartTag. Para obtener más información, vea los temas siguientes:  
  
-   [Actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Actualizar las personalizaciones de la cinta de opciones en proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Actualizar las áreas de formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Nuevas clases base en proyectos de Office  
 El nuevo diseño basado en interfaces del Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office afecta a las clases generadas en proyectos de Office, como `ThisDocument`, `ThisWorkbook`y `ThisAddIn`. En proyectos de Office destinados a .NET Framework 3.5 y versiones anteriores de framework, estas clases generadas se derivan de clases en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] como Microsoft.Office.Tools.Word.Document, Microsoft.Office.Tools.Excel.Worksheet, y Microsoft.Office.Tools.AddIn. En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, estas clases [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] son interfaces. Por lo tanto, las clases generadas en proyectos de Office ya no pueden derivar su implementación de ellas. En su lugar, las clases generadas derivan de nuevas clases base como <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>y <xref:Microsoft.Office.Tools.AddInBase>. Para obtener más información, vea [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md) y [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Las clases base no forman parte de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuible. En su lugar, se definen en ensamblados de utilidades incluidos en Visual Studio. Estos ensamblados se copian en la carpeta de salida al compilar proyectos de Office y se deben implementar con la solución. Para obtener más información sobre los ensamblados de utilidades, vea [Assemblies in the Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Cambios importantes en los proyectos de Office que se redestinan a .NET Framework 4  
 En la tabla siguiente se enumeran los principales cambios importantes que se puede encontrar en los proyectos de Office que se redestinan a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Para obtener más detalles, vea [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Cambio importante|Consecuencia|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> ya no se usa o no se admite en proyectos de Office.|Debe quitar este atributo del archivo de código AssemblyInfo de los proyectos de Office que actualice desde Visual Studio 2008. Para obtener más información, consulte [cambios necesarios para la ejecución de proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Ya no se usa el ExcelLocale1033Attribute o se admite en proyectos de Excel.|Debe quitar este atributo del archivo de código AssemblyInfo de los proyectos de Excel. Para obtener más información, consulte [actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|El modelo de programación de elementos de proyecto de la **Cinta (diseñador visual)** ha cambiado.|Debe modificar el archivo de código subyacente de los elementos de la cinta de opciones del proyecto. También debe modificar cualquier código que cree instancias de controles de la cinta de opciones en tiempo de ejecución, controle eventos de la cinta de opciones o establezca la posición de un componente de la cinta de opciones mediante programación. Para obtener más información, consulte [actualizar las personalizaciones de la cinta de opciones en Office proyectos para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Ha cambiado el modelo de programación de las áreas de formulario de Outlook.|Debe modificar el archivo de código subyacente de cualquier área de formulario del proyecto y de cualquier código que cree instancias de determinadas clases de área de formulario en tiempo de ejecución. Para obtener más información, consulte [actualizar las áreas de formulario en Outlook proyectos para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Ha cambiado el modelo de programación de las etiquetas inteligentes en proyectos de Excel y Word. Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Si la solución utiliza etiquetas inteligentes, se producirán errores al compilar el proyecto. Como las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], tiene que quitarlas para probar y depurar la solución en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o versiones posteriores.|  
|Ha cambiado la sintaxis de los métodos HasVstoObject y GetVstoObject|Debe pasar el objeto Globals.Factory a estos métodos cuando se accede a ellos en objetos nativos de los ensamblados de interoperabilidad primarios (PIA), o puede tener acceso a estos métodos en el objeto devuelto por la propiedad Globals.Factory en el proyecto. Para obtener más información, consulte [actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Los eventos de controles de contenido de Word se asocian a nuevos delegados.|Tiene que modificar el código que controle eventos de controles de contenido de Word para especificar los nuevos delegados. Para obtener más información, consulte [actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Las clases OLEObject y OLEControl han cambiado de nombre.|Tiene que modificar cualquier código que use instancias de estas clases para utilizar los objetos <xref:Microsoft.Office.Tools.Excel.ControlSite> o <xref:Microsoft.Office.Tools.Word.ControlSite> en su lugar. Para obtener más información, consulte [actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Clases de elemento host como `ThisWorkbook`, `Sheet`  *n* , `ThisDocument`, y `ThisAddIn`, dejará de proporcionar un método Dispose que se pueda reemplazar.|Debe migrar cualquier código en la invalidación del método Dispose en el controlador de eventos de apagado de la clase de elemento host, por ejemplo, `ThisAddIn_Shutdown`y quitar la invalidación del método Dispose de la clase de elemento host.|  
  
## <a name="see-also"></a>Vea también  
 [Migración de soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Novedades en el desarrollo de Office](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Información general sobre el motor en tiempo de ejecución de Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  