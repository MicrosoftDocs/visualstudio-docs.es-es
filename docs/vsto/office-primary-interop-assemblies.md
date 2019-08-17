---
title: ensamblados de interoperabilidad primarios de Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c1038d0d7e7d20c28cdd0cb52804461376a4e89
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551688"
---
# <a name="office-primary-interop-assemblies"></a>ensamblados de interoperabilidad primarios de Office

Para usar las características de una aplicación de Microsoft Office desde un proyecto de Office, debe usar el ensamblado de interoperabilidad primario (PIA) de la aplicación. El PIA permite que el código administrado interactúe con el modelo de objetos basado en COM de una aplicación de Microsoft Office.

[!include[Add-ins note](includes/addinsnote.md)]

Al crear un proyecto de Office, Visual Studio agrega referencias a los PIA obligatorios para compilar el proyecto. En algunos escenarios, es posible que deba agregar referencias a PIA adicionales (por ejemplo, si desea usar una característica de Microsoft Office Word en un proyecto para Microsoft Office Excel).

En este tema se describen los aspectos siguientes del uso de PIA de Microsoft Office en proyectos de Office:

- [Ensamblados de interoperabilidad primarios independientes para compilar y ejecutar proyectos](#separateassemblies)

- [Usar características de varias aplicaciones de Microsoft Office en un solo proyecto](#usingfeatures)

- [Lista completa de ensamblados de interoperabilidad primarios para aplicaciones de Microsoft Office](#pialist)

Para más información sobre los ensamblados de interoperabilidad primarios, vea ensamblados de interoperabilidad [primarios](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Ensamblados de interoperabilidad primarios independientes para compilar y ejecutar proyectos

Visual Studio usa conjuntos distintos de los PIA en el equipo de desarrollo. Estos conjuntos distintos de ensamblados se encuentran en las ubicaciones siguientes:

- Una carpeta en el directorio archivos de programa

  Estas copias de los ensamblados se usan al escribir código y compilar proyectos. Visual Studio instala estos ensamblados automáticamente.

- La caché global de ensamblados

  Estas copias de los ensamblados se usan durante algunas tareas de desarrollo, como al ejecutar o depurar proyectos. Visual Studio no instala y registra estos ensamblados; debe hacerlo el usuario.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Ensamblados de interoperabilidad primarios en el directorio de archivos de programa

Al instalar Visual Studio, los PIA se instalan automáticamente en una ubicación del sistema de archivos, fuera de la caché global de ensamblados. Al crear un proyecto, Visual Studio agrega automáticamente referencias a estas copias de los PIA al proyecto. Visual Studio usa estas copias de los PIA, en lugar de los ensamblados de la caché global de ensamblados, para resolver referencias a tipos al desarrollar y compilar el proyecto.

Estas copias de los PIA ayudan a Visual Studio a evitar varios problemas de desarrollo que se pueden producir cuando se registran distintas versiones de los PIA en la caché global de ensamblados.

A partir de Visual Studio 2017, estas copias de los PIA se instalan en las siguientes ubicaciones compartidas en el equipo de desarrollo:

- *%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\*

- (o *% ProgramFiles (x86)% \ Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\* en sistemas operativos de 64 bits)

> [!NOTE]
> En el caso de las versiones anteriores de Visual Studio, estos Pia se instalarán en la carpeta Visual Studio Tools for Office\PIA en la carpeta *% ProgramFiles% de esa versión de Visual Studio.  
> Por ejemplo: *% ProgramFiles (x86)% \ Microsoft Visual Studio 14.0 \ Visual Studio Tools para Office\PIA\*

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Ensamblados de interoperabilidad primarios en la caché global de ensamblados

Para realizar ciertas tareas de desarrollo, los PIA deben estar instalados y registrados en la caché global de ensamblados del equipo de desarrollo. Normalmente, los PIA se instalan automáticamente al instalar Office en el equipo de desarrollo. Para obtener más información, vea [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

Los PIA de Office no son obligatorios en los equipos de los usuarios finales para ejecutar soluciones de Office. Para obtener más información, vea [diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Usar características de varias aplicaciones de Microsoft Office en un solo proyecto

Cada plantilla de proyecto de Office en Visual Studio está diseñada para funcionar con una sola aplicación de Microsoft Office. Para usar características de varias aplicaciones de Microsoft Office o para usar características de una aplicación o un componente que no tenga un proyecto en Visual Studio, debe agregar una referencia a los PIA necesarios.

En la mayoría de los casos, debe agregar referencias a los PIA que instala Visual Studio en el `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` directorio. Estas versiones de los ensamblados aparecen en la pestaña **marco** del cuadro de diálogo **Administrador de referencias** . Para obtener más información, consulte [Cómo Aplicaciones de Office de destino a través](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)de ensamblados de interoperabilidad primarios

Si ha instalado y registrado los PIA en la caché global de ensamblados, estas versiones de los ensamblados aparecen en la pestaña **COM** del cuadro de diálogo **Administrador de referencias** . Debe evitar agregar referencias a estas versiones de los ensamblados, puesto que se pueden producir algunos problemas de desarrollo al usarlas. Por ejemplo, si ha registrado distintas versiones de los PIA en la caché global de ensamblados, el proyecto se enlazará automáticamente a la última versión del ensamblado que se registró, aunque especifique una versión distinta en la pestaña **COM** del cuadro de diálogo **Administrador de referencias** .

> [!NOTE]
> Algunos ensamblados se agregan a un proyecto automáticamente cuando se agrega un ensamblado que hace referencia a ellos. Por ejemplo, las referencias a los ensamblados *Office. dll* y *Microsoft. Vbe. Interop. dll* se agregan automáticamente al agregar una referencia a los ensamblados de Word, Excel, Outlook, Microsoft Forms o Graph.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Ensamblados de interoperabilidad primarios para aplicaciones Microsoft Office

En la tabla siguiente se enumeran los ensamblados de interoperabilidad [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]primarios disponibles para [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y.

<br/>

|Aplicación o componente de Office|Nombre del ensamblado de interoperabilidad primario|
|-------------------------------------|-----------------------------------|
|Biblioteca de objetos de Microsoft Access 14.0<br /><br /> Biblioteca de objetos de Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|
|Biblioteca de objetos del motor de base de datos de Access de Microsoft Office 14.0<br /><br /> Biblioteca de objetos del motor de base de datos de Access de Microsoft Office 15.0|Microsoft.Office.Interop.Access.Dao.dll|
|Biblioteca de objetos de Microsoft Excel 14.0<br /><br /> Biblioteca de objetos de Microsoft Excel 15.0|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|
|Biblioteca de objetos de Microsoft Graph 14.0 (usada por PowerPoint, Access y Word para gráficos)<br /><br /> Biblioteca de objetos de Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|
|Biblioteca de tipos de Microsoft InfoPath 2.0 (solo para InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|
|Ensamblado de interoperabilidad XML de Microsoft InfoPath (solo para InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|
|Biblioteca de objetos de Microsoft Office 14.0 (funcionalidad compartida de Office)<br /><br /> Biblioteca de objetos de Microsoft Office 15.0 (funcionalidad compartida de Office)|office.dll|
|Control de vistas de Microsoft Office Outlook (se puede usar en páginas web y aplicaciones para tener acceso a la Bandeja de entrada)|Microsoft.Office.Interop.OutlookViewCtl.dll|
|Biblioteca de objetos de Microsoft Outlook 14.0<br /><br /> Biblioteca de objetos de Microsoft Outlook 15.0|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|
|Biblioteca de objetos de Microsoft PowerPoint 14.0<br /><br /> Biblioteca de objetos de Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|
|Biblioteca de objetos de Microsoft Project 14.0<br /><br /> Biblioteca de objetos de Microsoft Project 15.0|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|
|Biblioteca de objetos de Microsoft Publisher 14.0<br /><br /> Biblioteca de objetos de Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|
|Biblioteca de referencia de objetos web de Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesigner.dll|
|Biblioteca de referencia de objetos de página de Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesignerPage.dll|
|Biblioteca de tipos de Microsoft Smart Tags 2,0 **Nota:**  Las etiquetas inteligentes están desusadas en [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] y [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|
|Biblioteca de tipos de Microsoft Visio 14.0<br /><br /> Biblioteca de tipos de Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.dll|
|Biblioteca de tipos Guardar como web de Microsoft Visio 14.0<br /><br /> Biblioteca de tipos Guardar como web de Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|
|Biblioteca de tipos de control de dibujo de Microsoft Visio 14.0<br /><br /> Biblioteca de tipos de control de dibujo de Microsoft Visio 15.0|Microsoft.Office.Interop.VisOcx.dll|
|Biblioteca de objetos de Microsoft Word 14.0<br /><br /> Biblioteca de objetos de Microsoft Word 15.0|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|
|Extensibilidad de Microsoft Visual Basic para Aplicaciones 5.3|Microsoft.Vbe.Interop.dll|

### <a name="binding-redirect-assemblies"></a>Enlazar ensamblados de redirección

Al instalar y registrar los PIA de Office en la caché global de ensamblados (con Office o por medio de la instalación del paquete redistribuible para los PIA), los ensamblados de redirección de enlace también se instalan solamente en la caché global de ensamblados. Estos ensamblados ayudan a asegurarse de que se carga la versión correcta de los ensamblados de interoperabilidad primarios en tiempo de ejecución.

Por ejemplo, cuando una solución que hace referencia a un ensamblado de [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] se ejecuta en un equipo con la versión de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] del ensamblado de interoperabilidad primario, el ensamblado de redirección de enlace indica al tiempo de ejecución de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] que cargue la versión de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] del ensamblado de interoperabilidad primario.

Para obtener más información, vea [Cómo: Habilitar y deshabilitar la redirección](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection)de enlace automática.

## <a name="see-also"></a>Vea también

- [Cómo: Aplicaciones de Office de destino a través de ensamblados de interoperabilidad principales](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Información general del modelo de objetos de Excel](../vsto/excel-object-model-overview.md)
- [Soluciones de InfoPath](../vsto/infopath-solutions.md)
- [Información general del modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)
- [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)
- [Soluciones de proyecto](../vsto/project-solutions.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Desarrollo de &#40;Office de referencia general en Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)
