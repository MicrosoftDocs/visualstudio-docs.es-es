---
title: Información general sobre el tiempo de ejecución de Visual Studio Tools para Office
description: Visual Studio 2010 Tools para Office Runtime debe estar instalado en los equipos de los usuarios finales para ejecutar soluciones creadas con las herramientas de desarrollo de Microsoft Office.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 16431a9ba2fe56b88f9f6b7f2c874c75bfad61c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526274"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Información general sobre el tiempo de ejecución de Visual Studio Tools para Office
  Para ejecutar soluciones creadas con las herramientas de desarrollo de Microsoft Office en Visual Studio, se debe instalar Visual Studio 2010 Tools para Office Runtime en los equipos de los usuarios finales. Para obtener más información, vea [Cómo: instalar el Visual Studio Tools para Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). El tiempo de ejecución de Visual Studio 2010 Tools para Office consta de dos componentes principales:

- Las extensiones de Office para .NET Framework. Estos componentes son ensamblados administrados que proporcionan la capa de comunicación entre la solución y la aplicación de Microsoft Office. Para obtener más información, consulte Descripción de las [extensiones de Office para el .NET Framework](#officeextensions).

- El cargador de solución de Office. Este componente es un conjunto de DLL no administradas que las aplicaciones de Office usan para cargar el runtime y las soluciones. Para obtener más información, vea [Descripción del cargador de soluciones de Office](#UnmanagedLoader).

  El runtime se puede instalar de varias maneras diferentes. Dependiendo de la configuración del equipo, se instalan distintos componentes en tiempo de ejecución al instalar el runtime. Para obtener más información, vea [Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="understand-the-office-extensions-for-the-net-framework"></a><a name="officeextensions"></a> Descripción de las extensiones de Office para el .NET Framework
 Visual Studio 2010 Tools para Office Runtime incluye las extensiones de Office para el .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y versiones posteriores. Las soluciones destinadas a cada versión de .NET Framework usan las extensiones correspondientes para esa versión.

 Estas extensiones están formadas por ensamblados que las soluciones usan para automatizar y extender las aplicaciones de Office. Al crear un proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados correspondientes al tipo de proyecto y la versión de .NET Framework de destino del proyecto. Para obtener más información sobre los ensamblados de las extensiones de Office, vea [ensamblados en la Visual Studio Tools de tiempo de ejecución de Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Diferencias de diseño en las extensiones de Office
 La mayoría de los tipos que utiliza en las extensiones de Office para .NET Framework 3.5 son clases. Estas son las mismas clases que se incluían en versiones anteriores de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. En cambio, la mayoría de los tipos que se utilizan en las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores son interfaces. Por ejemplo, cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos <xref:Microsoft.Office.Tools.Excel.Worksheet> y <xref:Microsoft.Office.Tools.Word.Document> son interfaces en lugar de clases.

 En la mayoría de los casos, el código que se escribe en las soluciones de Office es el mismo con independencia de si la versión de destino de la solución es .NET Framework 3.5 o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Sin embargo, ciertas características requieren código diferente para cada versión de .NET Framework. Para obtener más información, vea [migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfaces de las extensiones de Office para el .NET Framework 4 o posterior
 La mayoría de las interfaces de las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores no se han diseñado para que se implementen mediante código de usuario. Las únicas interfaces que puede implementar directamente tienen nombres que comienzan por la letra **I**, como <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.

 Todas las interfaces que no comienzan por la letra **I** se implementan internamente con Visual Studio 2010 Tools para Office Runtime, y estas interfaces pueden cambiar en futuras versiones. Para crear objetos que implementan estas interfaces, utilice métodos proporcionados por el objeto `Globals.Factory` en su proyecto. Por ejemplo, para obtener un objeto que implemente la interfaz <xref:Microsoft.Office.Tools.Excel.SmartTag>, utilice el método `Globals.Factory.CreateSmartTag`. Para obtener más información sobre `Globals.Factory` , consulte [acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Habilitar la equivalencia de tipos y tipos incrustados en proyectos que tienen como destino el .NET Framework 4 o posterior
 Puesto que el modelo de objetos de las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores se basa en interfaces, puede utilizar la característica de equivalencia de tipos de Visual C# y Visual Basic en Visual Studio para incrustar información de tipos desde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en la solución. Esta característica permite a las soluciones de Office y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] controlar las versiones de manera independiente. Por ejemplo, si su solución utiliza la interfaz <xref:Microsoft.Office.Tools.Word.Document> como tipo incrustado y la versión siguiente del runtime agrega miembros a la interfaz <xref:Microsoft.Office.Tools.Word.Document> , la solución seguirá funcionando con la versión siguiente del runtime. Si la solución no utiliza la interfaz <xref:Microsoft.Office.Tools.Word.Document> como tipo incrustado, entonces la solución ya no funcionará con la versión siguiente del runtime.

 De forma predeterminada, la característica de equivalencia de tipos no está habilitada al crear un proyecto de Office cuyo destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Si desea habilitar esta característica, establezca la propiedad **Incrustar tipos de interoperabilidad** de cualquiera de las siguientes referencias de ensamblado del proyecto en **True**:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Después de realizar esta modificación, la información de tipo para todos los tipos en tiempo de ejecución utilizados por el proyecto se incrusta en el ensamblado de la solución al compilar el proyecto. La solución utiliza esta información de tipo incrustada en tiempo de ejecución, en lugar de la información de tipo de los ensamblados a los que se hace referencia.

## <a name="understand-the-office-solution-loader"></a><a name="UnmanagedLoader"></a> Descripción del cargador de soluciones de Office
 El Runtime de Microsoft Visual Studio Tools para Office incluye varias DLL no administradas que las aplicaciones de Office usan para cargar el runtime y las soluciones de Office. Aunque nunca debería tener que trabajar directamente con estas DLL, conocer su finalidad puede ayudarle a entender mejor la arquitectura de las soluciones de Office.

 Para obtener información sobre cómo se utilizan estos componentes durante el proceso de carga, vea [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md) y [arquitectura de los complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="vstoeedll"></a>vstoee.dll
 Cuando un usuario abre una personalización de nivel de documento o inicia un complemento de VSTO, la aplicación de Office llama a *VSTOEE.dll* para realizar las tareas necesarias para cargar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 *VSTOEE.dll* garantiza que se cargue la versión correcta de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para la solución y la versión instalada de Office. Aunque [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] se pueden instalar varias versiones de en el mismo equipo, solo se instala una instancia de *VSTOEE.dll* a la vez. Este es el *VSTOEE.dll* que se incluyó con la versión más reciente del motor en tiempo de ejecución instalada en el equipo. Para obtener más información sobre las distintas versiones de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que se pueden usar para otras soluciones, vea [ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 Después de que *VSTOEE.dll* carga la versión adecuada de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , *VSTOLoader.dll* realiza la mayor parte del trabajo necesario para cargar el ensamblado de la solución. *VSTOLoader.dll* realiza varias acciones:

- Crea un dominio de aplicación para cada ensamblado de solución.

- Realiza un conjunto de comprobaciones de seguridad para comprobar que el ensamblado de solución tiene permiso para ejecutarse.

- Carga la versión de las extensiones de Office para .NET Framework que requiere la solución.

  *VSTOLoader.dll* también realiza varias acciones específicas de los complementos de VSTO:

- Implementa la interfaz <xref:Extensibility.IDTExtensibility2> . <xref:Extensibility.IDTExtensibility2> es una interfaz COM que deben implementar todos los complementos de VSTO para aplicaciones de Microsoft Office. Esta interfaz define métodos a los que la aplicación llama para comunicar con el complemento de VSTO.

- Implementa la interfaz IManagedAddin. Las aplicaciones de Office usan esta interfaz para ayudar a cargar los complementos de VSTO. Para obtener más información, consulte [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Comprender las versiones de 32 bits y 64 bits del motor en tiempo de ejecución
 Hay versiones independientes de 64 y 32 bits de Visual Studio 2010 Tools para Office Runtime. Estas versiones del runtime se utilizan para ejecutar soluciones en las ediciones de 64 bits y de 32 bits de Office. La siguiente tabla muestra qué versión del runtime es necesaria para cada combinación de Windows y Office.

|Edición de Windows|Edición de Microsoft Office|Versión obligatoria de Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32 bits|32 bits|32 bits|
|64 bits|32 bits|64 bits|
|64 bits|64 bits|64 bits|

 Al instalar Office, se instala la versión necesaria de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] junto con Office. Por ejemplo, al instalar la edición de 64 bits de Office en una versión de 64 bits de Windows, también se instala la versión de 64 bits de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Para obtener más información sobre la instalación de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] con Office, vea [Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 La versión de 64 bits de Office también puede ejecutar soluciones de Office creadas con plantillas de proyecto de 2007 Microsoft Office system en Visual Studio 2008. Sin embargo, no puede ejecutar soluciones de Office creadas con plantillas de proyecto para Microsoft Office 2003 en Visual Studio 2008 o soluciones de Office creadas con Visual Studio 2005. Para obtener más información, vea [ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Reparación del tiempo de ejecución de Visual Studio 2010 Tools para Office
 Si necesita reparar el runtime, abra **Programas y características** o **Agregar o quitar programas** en el Panel de control, seleccione **Runtime de Microsoft Visual Studio 2010 Tools para Office** en la lista de programas y, a continuación, haga clic en **Desinstalar**. El programa de instalación que se ejecuta permite reparar el runtime. Si hace clic en **Cambiar**, no tendrá la opción de reparar el runtime.

## <a name="see-also"></a>Consulte también
- [Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Ensamblados en el Visual Studio Tools para Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md)
