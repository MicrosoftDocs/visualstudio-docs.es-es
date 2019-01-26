---
title: Cambios en el diseño de proyectos de Office que tienen como destino .NET Framework
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9d1297c30813cf9cecb2484f75420bed0b140bf
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876296"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Cambios en el diseño de proyectos de Office que tienen como destino .NET Framework 4 o .NET Framework 4.5
  A partir de [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio introdujo algunos cambios en el diseño de los proyectos de Office destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Si está familiarizado con los proyectos de Office en versiones anteriores de Visual Studio, debe tener en cuenta estos cambios a la hora de desarrollar proyectos de Office destinados a esas versiones de .NET Framework 4.0 o versiones posteriores. De forma predeterminada, todos los proyectos creados con Visual Studio 2013 o versiones posteriores van destinados a .NET Framework 4.0 o versiones posteriores.  
  
 En las secciones siguientes se describen estos cambios de diseño de los proyectos de Office.  
  
## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Entender el diseño basado en la interfaz de Visual Studio 2010 Tools para Office runtime  
 Al desarrollar un proyecto de Office que tenga como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, la mayoría de los tipos que usan en Visual Studio 2010 Tools para Office runtime es interfaces. Este es un importante cambio con respecto a las versiones anteriores del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], donde estos tipos eran clases. Por ejemplo, cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos <xref:Microsoft.Office.Tools.Excel.Worksheet> y <xref:Microsoft.Office.Tools.Word.Document> son interfaces en lugar de clases. Para obtener más información, consulte [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 En los tipos cuya instancia se podía crear directamente en las versiones anteriores del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], ahora se usan métodos del objeto `Globals.Factory` para obtener las instancias. Por ejemplo, para obtener un objeto que implemente la interfaz <xref:Microsoft.Office.Tools.Excel.SmartTag>, utilice el método `Globals.Factory.CreateSmartTag`. Para obtener más información, vea los temas siguientes:  
  
-   [Actualizar proyectos de Excel y Word migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Actualizar las personalizaciones de cinta de opciones en proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)  
  
-   [Actualizar las áreas de formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Nuevas clases base en proyectos de Office  
 El nuevo diseño basado en la interfaz de Visual Studio 2010 Tools para Office runtime afecta a las clases generadas en proyectos de Office, como `ThisDocument`, `ThisWorkbook`, y `ThisAddIn`. En proyectos de Office destinados a .NET Framework 3.5 y versiones anteriores de Framework, estas clases generadas derivan de clases del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], como `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet` y `Microsoft.Office.Tools.AddIn`. En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, estas clases [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] son interfaces. Por lo tanto, las clases generadas en proyectos de Office ya no pueden derivar su implementación de ellas. En su lugar, las clases generadas derivan de nuevas clases base como <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>y <xref:Microsoft.Office.Tools.AddInBase>. Para obtener más información, consulte [complementos VSTO programa](../vsto/programming-vsto-add-ins.md) y [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
 Las clases base no forman parte de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuible. En su lugar, se definen en ensamblados de utilidades incluidos en Visual Studio. Estos ensamblados se copian en la carpeta de salida al compilar proyectos de Office y se deben implementar con la solución. Para obtener más información acerca de los ensamblados de utilidades, consulte [ensamblados en Visual Studio Tools para Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Cambios importantes en los proyectos de Office que se redestinan a .NET Framework 4  
 En la tabla siguiente se enumeran los principales cambios importantes que se puede encontrar en los proyectos de Office que se redestinan a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Para obtener más información, consulte [soluciones de Office de migrar a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Cambio importante|Consecuencia|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> ya no se usa o no se admite en proyectos de Office.|Debe quitar este atributo del archivo de código AssemblyInfo de los proyectos de Office que actualice desde Visual Studio 2008. Para obtener más información, consulte [los cambios requeridos para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|El **ExcelLocale1033Attribute** ya no usa ni admite en proyectos de Excel.|Debe quitar este atributo desde el *AssemblyInfo* archivo de código en proyectos de Excel. Para obtener más información, consulte [actualización Excel y Word proyectos migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|El modelo de programación de elementos de proyecto de la **Cinta (diseñador visual)** ha cambiado.|Debe modificar el archivo de código subyacente de los elementos de la cinta de opciones del proyecto. También debe modificar cualquier código que cree instancias de controles de cinta de opciones en tiempo de ejecución, controla los eventos de la cinta de opciones o establece la posición de un componente de la cinta de opciones mediante programación. Para obtener más información, consulte [personalizaciones de cinta de opciones de actualización en los proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5).|  
|Ha cambiado el modelo de programación de las áreas de formulario de Outlook.|Debe modificar el archivo de código subyacente para las áreas de formulario en el proyecto y cualquier código que cree instancias de determinadas clases de área de formulario en tiempo de ejecución. Para obtener más información, consulte [actualizar las áreas de formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Ha cambiado el modelo de programación de las etiquetas inteligentes en proyectos de Excel y Word. Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Si la solución utiliza etiquetas inteligentes, se producirán errores al compilar el proyecto. Como las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], tiene que quitarlas para probar y depurar la solución en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o versiones posteriores.|  
|Ha cambiado la sintaxis de los métodos `GetVstoObject` y `HasVstoObject`.|Tiene que pasar el objeto `Globals.Factory` a estos métodos cuando obtenga acceso a ellos en objetos nativos desde los ensamblados de interoperabilidad primarios (PIA) o puede obtener acceso a estos métodos en el objeto devuelto por la propiedad `Globals.Factory` en el proyecto. Para obtener más información, consulte [actualización Excel y Word proyectos migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Los eventos de controles de contenido de Word se asocian a nuevos delegados.|Tiene que modificar el código que controle eventos de controles de contenido de Word para especificar los nuevos delegados. Para obtener más información, consulte [actualización Excel y Word proyectos migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Se ha cambiado el nombre de las clases `OLEObject` y `OLEControl`.|Tiene que modificar cualquier código que use instancias de estas clases para utilizar los objetos <xref:Microsoft.Office.Tools.Excel.ControlSite> o <xref:Microsoft.Office.Tools.Word.ControlSite> en su lugar. Para obtener más información, consulte [actualización Excel y Word proyectos migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Host de las clases de elementos, como `ThisWorkbook`, `Sheet` *n*, `ThisDocument`, y `ThisAddIn`, dejará de proporcionar un `Dispose` método que se puede invalidar.|Tiene que migrar cualquier código del reemplazo del método `Dispose` al controlador de eventos `Shutdown` de la clase de elemento host, por ejemplo, `ThisAddIn_Shutdown`, y quitar el reemplazo del método `Dispose` de la clase de elemento host.|  
  
## <a name="see-also"></a>Vea también  
 [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Novedades de desarrollo de Office](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
