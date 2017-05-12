---
title: "Cambios en el dise&#241;o de proyectos de Office destinados a .NET Framework 4 o .NET Framework 4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Desarrollo de Office en Visual Studio, novedades"
  - "Lo nuevo [desarrollo de Office en Visual Studio]"
ms.assetid: 290f5cb4-e2ee-4ed8-987c-2f013405cee9
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Cambios en el dise&#241;o de proyectos de Office destinados a .NET Framework 4 o .NET Framework 4.5
  A partir de [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio introdujo algunos cambios en el diseño de los proyectos de Office destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Si está familiarizado con los proyectos de Office en versiones anteriores de Visual Studio, debe tener en cuenta estos cambios a la hora de desarrollar proyectos de Office destinados a esas versiones de .NET Framework 4.0 o versiones posteriores. De forma predeterminada, todos los proyectos creados con Visual Studio 2013 o versiones posteriores van destinados a .NET Framework 4.0 o versiones posteriores.  
  
 En las secciones siguientes se describen estos cambios de diseño de los proyectos de Office.  
  
## Introducción al diseño basado en interfaces del Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office  
 Al desarrollar un proyecto de Office destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, la mayoría de los tipos que se usan en el Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office son interfaces. Este es un importante cambio con respecto a las versiones anteriores del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], donde estos tipos eran clases. Por ejemplo, cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos <xref:Microsoft.Office.Tools.Excel.Worksheet> y <xref:Microsoft.Office.Tools.Word.Document> son interfaces en lugar de clases. Para obtener más información, consulta [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 En los tipos cuya instancia se podía crear directamente en las versiones anteriores del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], ahora se usan métodos del objeto Globals.Factory para obtener las instancias. Por ejemplo, para obtener un objeto que implemente la interfaz <xref:Microsoft.Office.Tools.Excel.SmartTag>, utilice el método Globals.Factory.CreateSmartTag. Para obtener más información, consulta los temas siguientes:  
  
-   [Actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Actualizar las personalizaciones de la Cinta en los proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Actualizar las áreas del formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### Nuevas clases base en proyectos de Office  
 El nuevo diseño basado en interfaces del Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office afecta a las clases generadas en proyectos de Office, como `ThisDocument`, `ThisWorkbook` y `ThisAddIn`. En proyectos de Office destinados a .NET Framework 3.5 y versiones anteriores de Framework, estas clases generadas derivan de clases del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], como Microsoft.Office.Tools.Word.Document, Microsoft.Office.Tools.Excel.Worksheet y Microsoft.Office.Tools.AddIn. En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, estas clases [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] son interfaces. Por lo tanto, las clases generadas en proyectos de Office ya no pueden derivar su implementación de ellas. En su lugar, las clases generadas derivan de nuevas clases base como <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase> y <xref:Microsoft.Office.Tools.AddInBase>. Para obtener más información, vea [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md) y [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
 Las clases base no forman parte de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuible. En su lugar, se definen en ensamblados de utilidades incluidos en Visual Studio. Estos ensamblados se copian en la carpeta de salida al compilar proyectos de Office y se deben implementar con la solución. Para obtener más información sobre los ensamblados de utilidades, vea [Ensamblados en el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## Cambios importantes en los proyectos de Office que se redestinan a .NET Framework 4  
 En la tabla siguiente se enumeran los principales cambios importantes que se puede encontrar en los proyectos de Office que se redestinan a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Vea [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md) para obtener información más detallada.  
  
|Cambio importante|Consecuencia|  
|-----------------------|------------------|  
|<xref:System.Security.SecurityTransparentAttribute> ya no se usa o no se admite en proyectos de Office.|Debe quitar este atributo del archivo de código AssemblyInfo de los proyectos de Office que actualice desde Visual Studio 2008. Para obtener más información, consulta [Cambios necesarios para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|ExcelLocale1033Attribute ya no se usa o no se admite en proyectos de Excel.|Debe quitar este atributo del archivo de código AssemblyInfo de los proyectos de Excel. Para obtener más información, consulta [Actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|El modelo de programación de elementos de proyecto de la **Cinta \(diseñador visual\)** ha cambiado.|Debe modificar el archivo de código subyacente de los elementos de la cinta de opciones del proyecto. También debe modificar cualquier código que cree instancias de controles de la cinta de opciones en tiempo de ejecución, controle eventos de la cinta de opciones o establezca la posición de un componente de la cinta de opciones mediante programación. Para obtener más información, consulta [Actualizar las personalizaciones de la Cinta en los proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Ha cambiado el modelo de programación de las áreas de formulario de Outlook.|Debe modificar el archivo de código subyacente de cualquier área de formulario del proyecto y de cualquier código que cree instancias de determinadas clases de área de formulario en tiempo de ejecución. Para obtener más información, consulta [Actualizar las áreas del formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Ha cambiado el modelo de programación de las etiquetas inteligentes en proyectos de Excel y Word. Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Si la solución utiliza etiquetas inteligentes, se producirán errores al compilar el proyecto. Como las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], tiene que quitarlas para probar y depurar la solución en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o versiones posteriores.|  
|Ha cambiado la sintaxis de los métodos GetVstoObject y HasVstoObject.|Tiene que pasar el objeto Globals.Factory a estos métodos cuando obtenga acceso a ellos en objetos nativos desde los ensamblados de interoperabilidad primarios \(PIA\) o puede obtener acceso a estos métodos en el objeto devuelto por la propiedad Globals.Factory en el proyecto. Para obtener más información, consulta [Actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Los eventos de controles de contenido de Word se asocian a nuevos delegados.|Tiene que modificar el código que controle eventos de controles de contenido de Word para especificar los nuevos delegados. Para obtener más información, consulta [Actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Se ha cambiado el nombre de las clases OLEObject y OLEControl.|Tiene que modificar cualquier código que use instancias de estas clases para utilizar los objetos <xref:Microsoft.Office.Tools.Excel.ControlSite> o <xref:Microsoft.Office.Tools.Word.ControlSite> en su lugar. Para obtener más información, consulta [Actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Las clases de elementos host, como `ThisWorkbook`, `Sheet`*n*, `ThisDocument` y `ThisAddIn`, ya no proporcionan ningún método Dispose que se pueda reemplazar.|Tiene que migrar cualquier código del reemplazo del método Dispose al controlador de eventos Shutdown de la clase de elemento host, por ejemplo, `ThisAddIn_Shutdown`, y quitar el reemplazo del método Dispose de la clase de elemento host.|  
  
## Vea también  
 [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Novedades en el desarrollo de aplicaciones para Office](http://msdn.microsoft.com/es-es/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  