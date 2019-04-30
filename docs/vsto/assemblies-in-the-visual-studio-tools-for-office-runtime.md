---
title: Ensamblados en Visual Studio Tools para Office runtime
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e4d9932e64cbbd862c5784073ed4dbe7cb85709
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944841"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Ensamblados en Visual Studio Tools para Office runtime
  Al crear un proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] correspondientes al tipo de proyecto y la versión de .NET Framework de destino del proyecto. Hay ensamblados distintos en las extensiones de Office para .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], y [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obtener más información acerca de las extensiones de Office, consulte [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Los ensamblados de las extensiones de Office para .NET Framework 4 y [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 La tabla siguiente enumera los ensamblados que se incluyen en las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obtener documentación sobre los espacios de nombres y tipos de estos ensamblados, consulte [referencia administrada de &#40;desarrollo de Office en Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).

|Nombre del ensamblado|Descripción|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Proporciona los tipos siguientes.<br /><br /> -Tipos para crear personalizaciones de cinta de opciones y etiquetas inteligentes. **Nota:**      Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Tipos para crear paneles de acciones en personalizaciones de nivel de documento y paneles de tareas personalizados en complementos VSTO.|
|Microsoft.Office.Tools.Excel.dll|Proporciona interfaces que representan elementos host y controles host de proyectos de Excel, así como los tipos compatibles. Para obtener más información, consulte [automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Proporciona tipos que puede usar para crear áreas de formulario personalizadas en complementos de VSTO de Outlook.|
|Microsoft.Office.Tools.Word.dll|Proporciona interfaces que representan elementos host y controles host de proyectos de Word, así como los tipos compatibles. Para obtener más información, consulte [automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Proporciona los tipos siguientes.<br /><br /> -Las excepciones que pueden iniciar Visual Studio Tools para Office runtime.<br />-Los atributos que puede usar al crear Outlook áreas de formulario.|
|Microsoft.Office.Tools.dll|Proporciona tipos que forman parte de la infraestructura del Runtime de Microsoft Visual Studio Tools para Office y no están diseñados para usarlos directamente en el código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Proporciona los tipos siguientes.<br /><br /> -El <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo y <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaz, que puede usar para los objetos de datos de caché en una personalización de nivel de documento. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).<br />-El <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfaz, que se puede implementar para ejecutar pasos de instalación adicionales como último paso del instalador de ClickOnce para una solución de Office. Para obtener más información, consulte [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Las excepciones que pueden iniciar Visual Studio Tools para Office runtime.<br />-Otros tipos que forman parte de Visual Studio Tools para la infraestructura de Office en tiempo de ejecución y no están diseñados para utilizarse directamente desde el código.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Proporciona los tipos siguientes.<br /><br /> -El <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (clase), que puede usar para adjuntar ensamblados de personalización a los documentos y tener acceso a los datos almacenados en caché de documentos. Para obtener más información, consulte [administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Varias clases que representan la jerarquía de datos en una personalización de nivel de documento almacenados en caché. Para obtener más información, consulte [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).|

 Los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] también hacen referencia a los ensamblados siguientes. Estos ensamblados no forman parte de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuible. Se trata de ensamblados dependientes que deben implementarse con la solución. De forma predeterminada, se copian en la carpeta de salida de compilación del proyecto (la propiedad **Copy Local** de estos ensamblados se establece en **True**). Si implementa el proyecto mediante ClickOnce, estos ensamblados se incluyen en el paquete generado.

|Nombre del ensamblado|Descripción|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Proporciona las clases base para la clase `ThisAddIn` generada en proyectos de complementos de VSTO y para la clase Ribbon generada en todos los proyectos.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Proporciona los tipos siguientes.<br /><br /> -Clases base para generado `ThisWorkbook` y `Sheet` las clases de nivel de documento proyectos para Excel.<br />-Controles de formularios de Windows que puede usar en las hojas de cálculo en proyectos de Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Proporciona clases base para las clases `ThisAddIn` y de área de formulario en los proyectos de Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Proporciona los tipos siguientes.<br /><br /> -Clases base para generado `ThisDocument` clase en los proyectos de nivel de documento para Word.<br />-Controles de formularios de Windows que puede usar en los documentos de proyectos de Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Ensamblados de las extensiones de Office para .NET Framework 3.5
 La tabla siguiente enumera los ensamblados que se incluyen en las extensiones de Office para .NET Framework 3.5. Para obtener documentación sobre las clases de estos ensamblados y espacios de nombres, vea la siguiente sección de referencia en la documentación de Visual Studio 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).

|Nombre del ensamblado|Descripción|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -La clase base Microsoft.Office.Tools.AddIn para complementos VSTO.<br />-Las clases para crear personalizaciones de cinta de opciones y etiquetas inteligentes. **Nota:**      Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Las clases para crear paneles de acciones en personalizaciones de nivel de documento y paneles de tareas personalizados en complementos VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Proporciona elementos host y controles host para las soluciones de Excel. Para obtener más información, consulte [automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Proporciona clases que puede usar para crear áreas de formulario personalizadas en complementos de VSTO de Outlook.|
|Microsoft.Office.Tools.Word.v9.0.dll|Proporciona elementos host y controles host para las soluciones de Word. Para obtener más información, consulte [automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -El [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) (clase), que proporciona las capacidades de enlace de datos para hospedar controles en personalizaciones de nivel de documento.<br />-Otros tipos que forman parte de Visual Studio Tools para la infraestructura de Office en tiempo de ejecución y no están diseñados para utilizarse directamente desde el código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -El <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo y <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaz, que puede usar para los objetos de datos de caché en una personalización de nivel de documento. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).<br />-Las excepciones que pueden iniciar Visual Studio Tools para Office runtime.<br />-Otros tipos que forman parte de Visual Studio Tools para la infraestructura de Office en tiempo de ejecución y no están diseñados para utilizarse directamente desde el código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Proporciona la interfaz <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, que puede implementar para ejecutar pasos de instalación adicionales como último paso del instalador de ClickOnce para una solución de Office. Para obtener más información, consulte [implementación de la solución avanzada de Office](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Proporciona los tipos siguientes.<br /><br /> -El <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (clase), que puede usar para adjuntar ensamblados de personalización mediante programación a documentos y tener acceso a los datos almacenados en caché de documentos. Para obtener más información, consulte [administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Varias clases que representan la jerarquía de datos en una personalización de nivel de documento almacenados en caché. Para obtener más información, consulte [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Proporciona los tipos siguientes.<br /><br /> -Las clases Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry y Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, que puede usar para crear entradas de la lista para conceder confianza a la oficina de inclusión de usuarios soluciones que tienen como destino .NET Framework 3.5.<br />-Otros tipos que forman parte de Visual Studio Tools para la infraestructura de Office en tiempo de ejecución y no están diseñados para utilizarse directamente desde el código.|

## <a name="see-also"></a>Vea también
- [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
