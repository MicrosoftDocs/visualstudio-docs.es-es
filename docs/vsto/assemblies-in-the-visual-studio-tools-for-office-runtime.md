---
title: Ensamblados en el Visual Studio Tools para Office Runtime
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
ms.openlocfilehash: b2fc47aa917fa9c9d5351fd313ec46ae4aaa0664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918783"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Ensamblados en el Visual Studio Tools para Office Runtime
  Al crear un proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] correspondientes al tipo de proyecto y la versión de .NET Framework de destino del proyecto. Hay ensamblados distintos en las extensiones de Office para .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], y [!INCLUDE[net_v45](includes/net-v45-md.md)]. Para obtener más información acerca de las extensiones de Office, vea [información general de Visual Studio Tools para Office Runtime](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>Los ensamblados de las extensiones de Office para el .NET Framework 4 y el [!INCLUDE[net_v45](includes/net-v45-md.md)]
 La tabla siguiente enumera los ensamblados que se incluyen en las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y [!INCLUDE[net_v45](includes/net-v45-md.md)]. Para obtener documentación sobre los espacios de nombres y los tipos de estos ensamblados, vea [referencia administrada &#40;desarrollo de Office en Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md).

|Nombre del ensamblado|Descripción|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Proporciona los tipos siguientes.<br /><br /> -Tipos para crear personalizaciones de la cinta de opciones y etiquetas inteligentes. **Nota:**      Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Tipos para crear paneles de acciones en personalizaciones de nivel de documento y paneles de tareas personalizados en complementos de VSTO.|
|Microsoft.Office.Tools.Excel.dll|Proporciona interfaces que representan elementos host y controles host de proyectos de Excel, así como los tipos compatibles. Para obtener más información, vea [automatizar Excel con objetos extendidos](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Proporciona tipos que puede usar para crear áreas de formulario personalizadas en complementos de VSTO de Outlook.|
|Microsoft.Office.Tools.Word.dll|Proporciona interfaces que representan elementos host y controles host de proyectos de Word, así como los tipos compatibles. Para obtener más información, vea [automatizar Word con objetos extendidos](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Proporciona los tipos siguientes.<br /><br /> : Excepciones que puede producir el Visual Studio Tools para Office Runtime.<br />-Atributos que se pueden usar al crear áreas de formulario de Outlook.|
|Microsoft.Office.Tools.dll|Proporciona tipos que forman parte de la infraestructura del Runtime de Microsoft Visual Studio Tools para Office y no están diseñados para usarlos directamente en el código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Proporciona los tipos siguientes.<br /><br /> -El <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo y la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaz, que puede usar para almacenar en memoria caché los objetos de datos en una personalización de nivel de documento. Para obtener más información, vea [almacenar datos en caché](caching-data.md).<br />-La <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfaz, que puede implementar para ejecutar pasos de instalación adicionales como último paso del instalador de ClickOnce para una solución de Office. Para obtener más información, vea [implementar una solución de Office mediante ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />: Excepciones que puede producir el Visual Studio Tools para Office Runtime.<br />-Otros tipos que forman parte de la Visual Studio Tools para la infraestructura de tiempo de ejecución de Office y no están diseñados para usarse directamente desde el código.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Proporciona los tipos siguientes.<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase, que puede usar para adjuntar los ensamblados de personalización a los documentos y para tener acceso a los datos almacenados en caché en documentos. Para obtener más información, vea [administrar documentos en un servidor mediante la clase ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Varias clases que representan la jerarquía de los datos almacenados en caché en una personalización de nivel de documento. Para obtener más información, vea [obtener acceso a los datos de documentos en el servidor](accessing-data-in-documents-on-the-server.md).|

 Los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](includes/net-v45-md.md)] también hacen referencia a los ensamblados siguientes. Estos ensamblados no forman parte de [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] redistribuible. Se trata de ensamblados dependientes que deben implementarse con la solución. De forma predeterminada, se copian en la carpeta de salida de compilación del proyecto (la propiedad **Copy Local** de estos ensamblados se establece en **True**). Si implementa el proyecto mediante ClickOnce, estos ensamblados se incluyen en el paquete generado.

|Nombre del ensamblado|Descripción|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Proporciona las clases base para la clase `ThisAddIn` generada en proyectos de complementos de VSTO y para la clase Ribbon generada en todos los proyectos.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Proporciona los tipos siguientes.<br /><br /> : Clases base para las `ThisWorkbook` clases y generadas en los proyectos de `Sheet` nivel de documento para Excel.<br />-Windows Forms controles que se pueden usar en hojas de cálculo de proyectos de Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Proporciona clases base para las clases `ThisAddIn` y de área de formulario en los proyectos de Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Proporciona los tipos siguientes.<br /><br /> : Clases base para la clase generada `ThisDocument` en los proyectos de nivel de documento para Word.<br />-Windows Forms controles que se pueden usar en los documentos de proyectos de Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Ensamblados de las extensiones de Office para el .NET Framework 3,5
 La tabla siguiente enumera los ensamblados que se incluyen en las extensiones de Office para .NET Framework 3.5. Para obtener documentación sobre los espacios de nombres y las clases de estos ensamblados, vea la siguiente sección de referencia en la documentación de Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Nombre del ensamblado|Descripción|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -La clase base Microsoft. Office. Tools. AddIn para los complementos de VSTO.<br />: Clases para crear personalizaciones de la cinta de opciones y etiquetas inteligentes. **Nota:**      Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />: Clases para crear paneles de acciones en personalizaciones de nivel de documento y paneles de tareas personalizados en complementos de VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Proporciona elementos host y controles host para las soluciones de Excel. Para obtener más información, vea [automatizar Excel con objetos extendidos](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Proporciona clases que puede usar para crear áreas de formulario personalizadas en complementos de VSTO de Outlook.|
|Microsoft.Office.Tools.Word.v9.0.dll|Proporciona elementos host y controles host para las soluciones de Word. Para obtener más información, vea [automatizar Word con objetos extendidos](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -La clase [RemoteBindableComponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) , que proporciona las funciones de enlace de datos para los controles host en las personalizaciones de nivel de documento.<br />-Otros tipos que forman parte de la Visual Studio Tools para la infraestructura de tiempo de ejecución de Office y no están diseñados para usarse directamente desde el código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Proporciona los tipos siguientes.<br /><br /> -El <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo y la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaz, que puede usar para almacenar en memoria caché los objetos de datos en una personalización de nivel de documento. Para obtener más información, vea [almacenar datos en caché](caching-data.md).<br />: Excepciones que puede producir el Visual Studio Tools para Office Runtime.<br />-Otros tipos que forman parte de la Visual Studio Tools para la infraestructura de tiempo de ejecución de Office y no están diseñados para usarse directamente desde el código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Proporciona la interfaz <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, que puede implementar para ejecutar pasos de instalación adicionales como último paso del instalador de ClickOnce para una solución de Office. Para obtener más información, vea [implementación avanzada de soluciones de Office](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Proporciona los tipos siguientes.<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase, que se puede usar para adjuntar mediante programación los ensamblados de personalización a los documentos y para tener acceso a los datos almacenados en caché en documentos. Para obtener más información, vea [administrar documentos en un servidor mediante la clase ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Varias clases que representan la jerarquía de los datos almacenados en caché en una personalización de nivel de documento. Para obtener más información, vea [obtener acceso a los datos de documentos en el servidor](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Proporciona los tipos siguientes.<br /><br /> -Las clases Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry y Microsoft. VisualStudio. Tools. Office. Runtime. Security. UserInclusionList, que puede usar para crear entradas de la lista de inclusión de usuarios para conceder confianza a las soluciones de Office destinadas a la .NET Framework 3,5.<br />-Otros tipos que forman parte de la Visual Studio Tools para la infraestructura de tiempo de ejecución de Office y no están diseñados para usarse directamente desde el código.|

## <a name="see-also"></a>Consulte también
- [Información general sobre el tiempo de ejecución de Visual Studio Tools para Office](visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office](visual-studio-tools-for-office-runtime-installation-scenarios.md)
