---
title: Visual Studio Tools para Office runtime overview
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7d3ba962a214f1f1ac9bf134a3408b38e8cb018
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868292"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio Tools para Office runtime overview
  Para ejecutar soluciones creadas mediante el uso de Microsoft Office developer tools en Visual Studio, Visual Studio 2010 Tools para Office runtime debe instalarse en equipos de usuario final. Para obtener más información, vea [Cómo: Instalar Visual Studio Tools para Office runtime redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools para Office runtime consta de dos componentes principales:  
  
- Las extensiones de Office para .NET Framework. Estos componentes son ensamblados administrados que proporcionan la capa de comunicación entre la solución y la aplicación de Microsoft Office. Para obtener más información, consulte [comprender las extensiones de Office para .NET Framework](#officeextensions).  
  
- El cargador de solución de Office. Este componente es un conjunto de DLL no administradas que las aplicaciones de Office usan para cargar el runtime y las soluciones. Para obtener más información, consulte [comprender el cargador de solución de Office](#UnmanagedLoader).  
  
  El runtime se puede instalar de varias maneras diferentes. Dependiendo de la configuración del equipo, se instalan distintos componentes en tiempo de ejecución al instalar el runtime. Para obtener más información, consulte [Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a> Comprender las extensiones de Office para .NET Framework  
 Visual Studio 2010 Tools para Office runtime incluye extensiones de Office para .NET Framework 3.5, el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y versiones posteriores. Las soluciones destinadas a cada versión de .NET Framework usan las extensiones correspondientes para esa versión.  
  
 Estas extensiones están formadas por ensamblados que las soluciones usan para automatizar y extender las aplicaciones de Office. Al crear un proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados correspondientes al tipo de proyecto y la versión de .NET Framework de destino del proyecto. Para obtener más información sobre los ensamblados en las extensiones de Office, consulte [ensamblados en Visual Studio Tools para Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### <a name="design-differences-in-the-office-extensions"></a>Diferencias de diseño en las extensiones de Office  
 La mayoría de los tipos que utiliza en las extensiones de Office para .NET Framework 3.5 son clases. Estas son las mismas clases que se incluían en versiones anteriores de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. En cambio, la mayoría de los tipos que se utilizan en las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores son interfaces. Por ejemplo, cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos <xref:Microsoft.Office.Tools.Excel.Worksheet> y <xref:Microsoft.Office.Tools.Word.Document> son interfaces en lugar de clases.  
  
 En la mayoría de los casos, el código que se escribe en las soluciones de Office es el mismo con independencia de si la versión de destino de la solución es .NET Framework 3.5 o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Sin embargo, ciertas características requieren código diferente para cada versión de .NET Framework. Para obtener más información, consulte [soluciones de Office de migrar a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfaces de las extensiones de Office para .NET Framework 4 o posterior  
 La mayoría de las interfaces de las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores no se han diseñado para que se implementen mediante código de usuario. Las únicas interfaces que puede implementar directamente tienen nombres que comienzan por la letra **I**, como <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 Todas las interfaces que no comienzan por la letra **me** se implementan internamente mediante Visual Studio 2010 Tools para Office runtime, y estas interfaces pueden cambiar en futuras versiones. Para crear objetos que implementan estas interfaces, utilice métodos proporcionados por el objeto `Globals.Factory` en su proyecto. Por ejemplo, para obtener un objeto que implemente la interfaz <xref:Microsoft.Office.Tools.Excel.SmartTag>, utilice el método `Globals.Factory.CreateSmartTag`. Para obtener más información acerca de `Globals.Factory`, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Habilitar la equivalencia de tipos y tipos incrustados en proyectos que tienen como destino .NET Framework 4 o posterior  
 Puesto que el modelo de objetos de las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores se basa en interfaces, puede utilizar la característica de equivalencia de tipos de Visual C# y Visual Basic en Visual Studio para incrustar información de tipos desde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en la solución. Esta característica permite a las soluciones de Office y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] controlar las versiones de manera independiente. Por ejemplo, si su solución utiliza la interfaz <xref:Microsoft.Office.Tools.Word.Document> como tipo incrustado y la versión siguiente del runtime agrega miembros a la interfaz <xref:Microsoft.Office.Tools.Word.Document> , la solución seguirá funcionando con la versión siguiente del runtime. Si la solución no utiliza la interfaz <xref:Microsoft.Office.Tools.Word.Document> como tipo incrustado, entonces la solución ya no funcionará con la versión siguiente del runtime.  
  
 De forma predeterminada, la característica de equivalencia de tipos no está habilitada al crear un proyecto de Office cuyo destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Si desea habilitar esta característica, establezca la propiedad **Incrustar tipos de interoperabilidad** de cualquiera de las siguientes referencias de ensamblado del proyecto en **True**:  
  
- Microsoft.Office.Tools.dll  
  
- Microsoft.Office.Tools.Common.dll  
  
- Microsoft.Office.Tools.Excel.dll  
  
- Microsoft.Office.Tools.Outlook.dll  
  
- Microsoft.Office.Tools.Word.dll  
  
  Después de realizar esta modificación, la información de tipo para todos los tipos en tiempo de ejecución utilizados por el proyecto se incrusta en el ensamblado de la solución al compilar el proyecto. La solución en tiempo de ejecución usa esta información de tipo incrustada, en lugar de la información de tipo en los ensamblados de referencia.  
  
##  <a name="UnmanagedLoader"></a> Comprender el cargador de solución de Office  
 El Runtime de Microsoft Visual Studio Tools para Office incluye varias DLL no administradas que las aplicaciones de Office usan para cargar el runtime y las soluciones de Office. Aunque nunca debería tener que trabajar directamente con estas DLL, conocer su finalidad puede ayudarle a entender mejor la arquitectura de las soluciones de Office.  
  
 Para obtener información acerca de cómo se utilizan estos componentes durante el proceso de carga, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md) y [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="vstoeedll"></a>vstoee.dll  
 Cuando un usuario abre una personalización de nivel de documento o inicia un complemento de VSTO, la aplicación de Office llama a *VSTOEE.dll* para realizar las tareas necesarias para cargar el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 *VSTOEE.dll* garantiza que la versión correcta de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] se carga para la solución y la versión instalada de Office. Aunque varias versiones de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] puede instalarse en el mismo equipo, solo una instancia de *VSTOEE.dll* está instalado en un momento. Se trata de la *VSTOEE.dll* que se incluyó con la versión más reciente del runtime instalada en el equipo. Para obtener más información sobre las diferentes versiones de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que puede usarse para otras soluciones, vea [ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 Después de *VSTOEE.dll* carga la versión adecuada de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], *VSTOLoader.dll* realiza la mayoría del trabajo necesario para cargar el ensamblado de solución. *VSTOLoader.dll* realiza varias acciones:  
  
- Crea un dominio de aplicación para cada ensamblado de solución.  
  
- Realiza un conjunto de comprobaciones de seguridad para comprobar que el ensamblado de solución tiene permiso para ejecutarse.  
  
- Carga la versión de las extensiones de Office para .NET Framework que requiere la solución.  
  
  *VSTOLoader.dll* también realiza varias tareas que son específicas de los complementos de VSTO:  
  
- Implementa la interfaz <xref:Extensibility.IDTExtensibility2> . <xref:Extensibility.IDTExtensibility2> es una interfaz COM que deben implementar todos los complementos de VSTO para aplicaciones de Microsoft Office. Esta interfaz define métodos a los que la aplicación llama para comunicar con el complemento de VSTO.  
  
- Implementa la interfaz IManagedAddin. Las aplicaciones de Office usan esta interfaz para ayudar a cargar los complementos de VSTO. Para obtener más información, consulte [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md).  
  
## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Comprender las versiones de 32 bits y 64 bits del tiempo de ejecución  
 Hay versiones independientes de 64 bits y 32 bits de Visual Studio 2010 Tools para Office runtime. Estas versiones del runtime se utilizan para ejecutar soluciones en las ediciones de 64 bits y de 32 bits de Office. La siguiente tabla muestra qué versión del runtime es necesaria para cada combinación de Windows y Office.  
  
|Edición de Windows|Edición de Microsoft Office|Versión obligatoria de Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32 bits|32 bits|32 bits|  
|64 bits|32 bits|64 bits|  
|64 bits|64 bits|64 bits|  
  
 Al instalar Office, se instala la versión necesaria de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] junto con Office. Por ejemplo, al instalar la edición de 64 bits de Office en una versión de 64 bits de Windows, también se instala la versión de 64 bits de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Para obtener más información acerca de cómo instalar el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] con Office, vea [Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 La versión de 64 bits de Office también puede ejecutar soluciones de Office creadas con plantillas de proyecto de 2007 Microsoft Office system en Visual Studio 2008. Sin embargo, no puede ejecutar soluciones de Office creadas con plantillas de proyecto para Microsoft Office 2003 en Visual Studio 2008 o soluciones de Office creadas con Visual Studio 2005. Para obtener más información, consulte [ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Reparar Visual Studio 2010 Tools para Office runtime  
 Si necesita reparar el runtime, abra **Programas y características** o **Agregar o quitar programas** en el Panel de control, seleccione **Runtime de Microsoft Visual Studio 2010 Tools para Office** en la lista de programas y, a continuación, haga clic en **Desinstalar**. El programa de instalación que se ejecuta permite reparar el runtime. Si hace clic en **Cambiar**, no tendrá la opción de reparar el runtime.  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Ensamblados en Visual Studio Tools para Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Arquitectura de soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md)  
