---
title: "Ensamblados en el Motor en tiempo de ejecuci&#243;n de Microsoft Visual Studio Tools para Office | Microsoft Docs"
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
  - "Visual Studio Tools para Office Runtime, ensamblados"
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Ensamblados en el Motor en tiempo de ejecuci&#243;n de Microsoft Visual Studio Tools para Office
  Al crear un proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] correspondientes al tipo de proyecto y la versión de .NET Framework de destino del proyecto. Hay ensamblados distintos en las extensiones de Office para .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], y [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obtener más información sobre las extensiones de Office, vea [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Ensamblados de las extensiones de Office para .NET Framework 4 y [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 La tabla siguiente enumera los ensamblados que se incluyen en las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obtener documentación sobre los espacios de nombres y tipos de estos ensamblados, vea [Referencia administrada &#40;desarrollo de Office en Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nombre del ensamblado|Descripción|  
|---------------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Proporciona los tipos siguientes.<br /><br /> -   Tipos para crear personalizaciones de la cinta de opciones y etiquetas inteligentes. **Note:**      Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-   Tipos para crear paneles de acciones en personalizaciones de nivel de documento y paneles de tareas personalizados en complementos de VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Proporciona interfaces que representan elementos host y controles host de proyectos de Excel, así como los tipos compatibles. Para obtener más información, consulta [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Proporciona tipos que puede usar para crear áreas de formulario personalizadas en complementos de VSTO de Outlook.|  
|Microsoft.Office.Tools.Word.dll|Proporciona interfaces que representan elementos host y controles host de proyectos de Word, así como los tipos compatibles. Para obtener más información, consulta [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Proporciona los tipos siguientes.<br /><br /> -   Excepciones que puede producir el Runtime de Microsoft Visual Studio Tools para Office.<br />-   Atributos que puede utilizar al crear áreas de formulario de Outlook.|  
|Microsoft.Office.Tools.dll|Proporciona tipos que forman parte de la infraestructura del Runtime de Microsoft Visual Studio Tools para Office y no están diseñados para usarlos directamente en el código.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Proporciona los tipos siguientes.<br /><br /> -   El atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> y la interfaz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, que puede usar para guardar en la memoria caché objetos de datos en una personalización de nivel de documento. Para obtener más información, consulta [Almacenar datos en caché](../vsto/caching-data.md).<br />-   La interfaz <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, que puede implementar para ejecutar pasos de instalación adicionales como último paso del instalador de ClickOnce para una solución de Office. Para obtener más información, consulta [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-   Excepciones que puede producir el Runtime de Microsoft Visual Studio Tools para Office.<br />-   Otros tipos que forman parte de la infraestructura del Runtime de Microsoft Visual Studio Tools para Office y no están diseñados para usarlos directamente en el código.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Proporciona los tipos siguientes.<br /><br /> -   La clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, que puede usar para adjuntar ensamblados de personalización a los documentos y para tener acceso a los datos almacenados en caché de documentos. Para obtener más información, consulta [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-   Varias clases que representan la jerarquía de los datos almacenados en caché en una personalización de nivel de documento. Para obtener más información, consulta [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] también hacen referencia a los ensamblados siguientes. Estos ensamblados no forman parte de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuible. Se trata de ensamblados dependientes que deben implementarse con la solución. De forma predeterminada, se copian en la carpeta de salida de compilación del proyecto \(la propiedad **Copy Local** de estos ensamblados se establece en **True**\). Si implementa el proyecto mediante ClickOnce, estos ensamblados se incluyen en el paquete generado.  
  
|Nombre del ensamblado|Descripción|  
|---------------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Proporciona las clases base para la clase `ThisAddIn` generada en proyectos de complementos de VSTO y para la clase Ribbon generada en todos los proyectos.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Proporciona los tipos siguientes.<br /><br /> -   Clases base para las clases `ThisWorkbook` y `Sheet` generadas en proyectos de nivel de documento para Excel.<br />-   Controles de formularios Windows Forms que puede utilizar en hojas de cálculo de proyectos para Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Proporciona clases base para las clases `ThisAddIn` y de área de formulario en los proyectos de Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Proporciona los tipos siguientes.<br /><br /> -   Clases base para la clase `ThisDocument` generada en proyectos de nivel de documento para Word.<br />-   Controles de formularios Windows Forms que puede utilizar en documentos de proyectos para Word.|  
  
## Ensamblados de las extensiones de Office para .NET Framework 3.5  
 La tabla siguiente enumera los ensamblados que se incluyen en las extensiones de Office para .NET Framework 3.5. Para informarse sobre los espacios de nombres y las clases de estos ensamblados, vea la siguiente sección de referencia en la documentación de Visual Studio 2008: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nombre del ensamblado|Descripción|  
|---------------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -   La clase base Microsoft.Office.Tools.AddIn para complementos de VSTO.<br />-   Clases para crear personalizaciones de la cinta de opciones y etiquetas inteligentes. **Note:**      Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-   Clases para crear paneles de acciones en personalizaciones de nivel de documento y paneles de tareas personalizados en complementos de VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Proporciona elementos host y controles host para las soluciones de Excel. Para obtener más información, consulta [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Proporciona clases que puede usar para crear áreas de formulario personalizadas en complementos de VSTO de Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Proporciona elementos host y controles host para las soluciones de Word. Para obtener más información, consulta [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -   La clase Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent, que proporciona las funciones de enlace de datos para los controles host en personalizaciones de nivel de documento.<br />-   Otros tipos que forman parte de la infraestructura del Runtime de Microsoft Visual Studio Tools para Office y no están diseñados para usarlos directamente en el código.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -   El atributo Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute y la interfaz Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType, que puede usar para guardar en la memoria caché objetos de datos en una personalización de nivel de documento. Para obtener más información, consulta [Almacenar datos en caché](../vsto/caching-data.md).<br />-   Excepciones que puede producir el Runtime de Microsoft Visual Studio Tools para Office.<br />-   Otros tipos que forman parte de la infraestructura del Runtime de Microsoft Visual Studio Tools para Office y no están diseñados para usarlos directamente en el código.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Proporciona la interfaz Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction, que puede implementar para ejecutar pasos de instalación adicionales como último paso del instalador de ClickOnce para una solución de Office. Para más información, vea [Implementación avanzada de soluciones de Office](http://msdn.microsoft.com/es-es/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Proporciona los tipos siguientes.<br /><br /> -   La clase Microsoft.VisualStudio.Tools.Applications.ServerDocument, que puede usar para adjuntar mediante programación ensamblados de personalización a los documentos y para tener acceso a los datos almacenados en caché de documentos. Para obtener más información, consulta [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-   Varias clases que representan la jerarquía de los datos almacenados en caché en una personalización de nivel de documento. Para obtener más información, consulta [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Proporciona los tipos siguientes.<br /><br /> -   Las clases Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry y Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, que puede usar para crear entradas de lista de inclusión de usuario para conceder confianza a las soluciones de Office destinados a .NET Framework 3.5.<br />-   Otros tipos que forman parte de la infraestructura del Runtime de Microsoft Visual Studio Tools para Office y no están diseñados para usarlos directamente en el código.|  
  
## Vea también  
 [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Escenarios de instalación del Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  