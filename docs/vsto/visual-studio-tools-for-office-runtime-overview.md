---
title: Visual Studio Tools para Office Runtime Overview | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
ms.assetid: 5526a4d2-a61c-43ee-8349-dd1968e0cdb4
caps.latest.revision: "92"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e091564ce02f55904e69d1abd9e240534a6dd8c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office
  Para ejecutar soluciones creadas con las Microsoft Office Developer Tools en Visual Studio, debe estar instalado Visual Studio 2010 Tools para Office Runtime en los equipos de los usuarios finales. Para obtener más información, consulta [How to: Install the Visual Studio Tools for Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). El Runtime de Microsoft Visual Studio 2010 Tools para Office consta de dos componentes principales:  
  
-   Las extensiones de Office para .NET Framework. Estos componentes son ensamblados administrados que proporcionan la capa de comunicación entre la solución y la aplicación de Microsoft Office. Para obtener más información, vea [Introducción a las extensiones de Office para .NET Framework](#officeextensions).  
  
-   El cargador de solución de Office. Este componente es un conjunto de DLL no administradas que las aplicaciones de Office usan para cargar el runtime y las soluciones. Para obtener más información, vea [Introducción al cargador de solución de Office](#UnmanagedLoader).  
  
 El runtime se puede instalar de varias maneras diferentes. Dependiendo de la configuración del equipo, se instalan distintos componentes en tiempo de ejecución al instalar el runtime. Para obtener más información, consulta [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a> Introducción a las extensiones de Office para .NET Framework  
 Visual Studio 2010 Tools para Office Runtime incluye las extensiones de Office para .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y versiones posteriores. Las soluciones destinadas a cada versión de .NET Framework usan las extensiones correspondientes para esa versión.  
  
 Estas extensiones están formadas por ensamblados que las soluciones usan para automatizar y extender las aplicaciones de Office. Al crear un proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados correspondientes al tipo de proyecto y la versión de .NET Framework de destino del proyecto. Para más información sobre los ensamblados en las extensiones de Office, vea [Assemblies in the Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### <a name="design-differences-in-the-office-extensions"></a>Diferencias de diseño en las extensiones de Office  
 La mayoría de los tipos que utiliza en las extensiones de Office para .NET Framework 3.5 son clases. Estas son las mismas clases que se incluían en versiones anteriores de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. En cambio, la mayoría de los tipos que se utilizan en las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores son interfaces. Por ejemplo, cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos <xref:Microsoft.Office.Tools.Excel.Worksheet> y <xref:Microsoft.Office.Tools.Word.Document> son interfaces en lugar de clases.  
  
 En la mayoría de los casos, el código que se escribe en las soluciones de Office es el mismo con independencia de si la versión de destino de la solución es .NET Framework 3.5 o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Sin embargo, ciertas características requieren código diferente para cada versión de .NET Framework. Para obtener más información, consulte [migrar soluciones de Office para .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfaces de las extensiones de Office para .NET Framework 4 o versiones posteriores  
 La mayoría de las interfaces de las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores no se han diseñado para que se implementen mediante código de usuario. Las únicas interfaces que puede implementar directamente tienen nombres que comienzan por la letra **I**, como <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 El Runtime de Microsoft Visual Studio 2010 Tools para Office implementa internamente todas las interfaces que no comienzan por la letra **I** , y estas interfaces pueden cambiar en futuras versiones. Para crear objetos que implementan estas interfaces, utilice métodos proporcionados por el objeto Globals.Factory en el proyecto. Por ejemplo, para obtener un objeto que implementa el <xref:Microsoft.Office.Tools.Excel.SmartTag> la interfaz, use el método Globals.Factory.CreateSmartTag. Para obtener más información acerca de Globals.Factory, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="enabling-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Habilitar la equivalencia de tipos y tipos incrustados en proyectos cuyo destino es .NET Framework 4 o versiones posteriores  
 Puesto que el modelo de objetos de las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores se basa en interfaces, puede utilizar la característica de equivalencia de tipos de Visual C# y Visual Basic en Visual Studio para incrustar información de tipos desde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en la solución. Esta característica permite a las soluciones de Office y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] controlar las versiones de manera independiente. Por ejemplo, si su solución utiliza la interfaz <xref:Microsoft.Office.Tools.Word.Document> como tipo incrustado y la versión siguiente del runtime agrega miembros a la interfaz <xref:Microsoft.Office.Tools.Word.Document> , la solución seguirá funcionando con la versión siguiente del runtime. Si la solución no utiliza la interfaz <xref:Microsoft.Office.Tools.Word.Document> como tipo incrustado, entonces la solución ya no funcionará con la versión siguiente del runtime.  
  
 De forma predeterminada, la característica de equivalencia de tipos no está habilitada al crear un proyecto de Office cuyo destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Si desea habilitar esta característica, establezca la propiedad **Incrustar tipos de interoperabilidad** de cualquiera de las siguientes referencias de ensamblado del proyecto en **True**:  
  
-   Microsoft.Office.Tools.dll  
  
-   Microsoft.Office.Tools.Common.dll  
  
-   Microsoft.Office.Tools.Excel.dll  
  
-   Microsoft.Office.Tools.Outlook.dll  
  
-   Microsoft.Office.Tools.Word.dll  
  
 Después de realizar esta modificación, la información de tipo para todos los tipos en tiempo de ejecución utilizados por el proyecto se incrusta en el ensamblado de la solución al compilar el proyecto. La solución utiliza esta información de tipo incrustada en tiempo de ejecución, en lugar de la información de tipo de los ensamblados a los que se hace referencia.  
  
##  <a name="UnmanagedLoader"></a> Introducción al cargador de solución de Office  
 El Runtime de Microsoft Visual Studio Tools para Office incluye varias DLL no administradas que las aplicaciones de Office usan para cargar el runtime y las soluciones de Office. Aunque nunca debería tener que trabajar directamente con estas DLL, conocer su finalidad puede ayudarle a entender mejor la arquitectura de las soluciones de Office.  
  
 Para obtener información sobre cómo se utilizan estos componentes durante el proceso de carga, vea [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md) y [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="vstoeedll"></a>vstoee.dll  
 Cuando un usuario abre una personalización de nivel de documento o inicia un complemento de VSTO, la aplicación de Office llama a VSTOEE.dll para realizar las tareas necesarias para cargar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 VSTOEE.dll se asegura de que se carga la versión correcta de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para la solución y la versión instalada de Office. Si bien en el equipo se pueden instalar varias versiones de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , no se instala más de una instancia de VSTOEE.dll a la vez. Esta versión corresponde al archivo VSTOEE.dll incluido con la última versión del motor en tiempo de ejecución instalado en el equipo. Para obtener más información sobre las distintas versiones de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que puede usar para otras soluciones, vea [ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 Después de que VSTOEE.dll carga la versión adecuada de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], VSTOLoader.dll realiza la mayoría del trabajo necesario para cargar el ensamblado de la solución. VSTOLoader.dll realiza varias acciones:  
  
-   Crea un dominio de aplicación para cada ensamblado de solución.  
  
-   Realiza un conjunto de comprobaciones de seguridad para comprobar que el ensamblado de solución tiene permiso para ejecutarse.  
  
-   Carga la versión de las extensiones de Office para .NET Framework que requiere la solución.  
  
 VSTOLoader.dll también realiza varias tareas específicas de los complementos de VSTO:  
  
-   Implementa la interfaz <xref:Extensibility.IDTExtensibility2> . <xref:Extensibility.IDTExtensibility2> es una interfaz COM que deben implementar todos los complementos de VSTO para aplicaciones de Microsoft Office. Esta interfaz define métodos a los que la aplicación llama para comunicar con el complemento de VSTO.  
  
-   Implementa la interfaz IManagedAddin. Las aplicaciones de Office usan esta interfaz para ayudar a cargar los complementos de VSTO. Para obtener más información, consulta [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
## <a name="understanding-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Introducción a las versiones de 32 bits y de 64 bits del runtime  
 Hay versiones 64 y 32 bits distintas del Runtime de Microsoft Visual Studio 2010 Tools para Office. Estas versiones del runtime se utilizan para ejecutar soluciones en las ediciones de 64 bits y de 32 bits de Office. La siguiente tabla muestra qué versión del runtime es necesaria para cada combinación de Windows y Office.  
  
|Edición de Windows|Edición de Microsoft Office|Versión obligatoria de Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32 bits|32 bits|32 bits|  
|64 bits|32 bits|64 bits|  
|64 bits|64 bits|64 bits|  
  
 Al instalar Office, se instala la versión necesaria de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] junto con Office. Por ejemplo, al instalar la edición de 64 bits de Office en una versión de 64 bits de Windows, también se instala la versión de 64 bits de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Para más información sobre la instalación de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] con Office, vea [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 La versión de 64 bits de Office también puede ejecutar soluciones de Office creadas con plantillas de proyecto de 2007 Microsoft Office system en Visual Studio 2008. Sin embargo, no puede ejecutar soluciones de Office creadas con plantillas de proyecto para Microsoft Office 2003 en Visual Studio 2008 o soluciones de Office creadas con Visual Studio 2005. Para obtener más información, consulte [ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## <a name="repairing-the-visual-studio-2010-tools-for-office-runtime"></a>Reparar Visual Studio 2010 Tools para Office Runtime  
 Si necesita reparar el runtime, abra **Programas y características** o **Agregar o quitar programas** en el Panel de control, seleccione **Runtime de Microsoft Visual Studio 2010 Tools para Office** en la lista de programas y, a continuación, haga clic en **Desinstalar**. El programa de instalación que se ejecuta permite reparar el runtime. Si hace clic en **Cambiar**, no tendrá la opción de reparar el runtime.  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Ensamblados en la Visual Studio Tools para Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Arquitectura de soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Actualización y migración de soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md)  
  
  