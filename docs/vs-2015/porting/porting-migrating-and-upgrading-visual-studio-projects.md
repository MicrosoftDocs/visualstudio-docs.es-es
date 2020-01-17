---
title: Portar, migrar y actualizar proyectos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 3361b04900e549d037338abfba0911b232c9e1bd
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919103"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Portar, migrar y actualizar proyectos de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [Referencia de migración y actualización de proyectos para Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Cuando considere la posibilidad de pasar a una versión más reciente de Visual Studio, puede usar este artículo para averiguar qué soluciones, proyectos, archivos y otros activos que creó en Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1 se ejecutarán sin modificaciones en Visual Studio 2013 y Visual Studio 2015. También es posible que haya llegado a esta página si se ha encontrado con un mensaje de error al intentar abrir un proyecto que no se admite en la versión de Visual Studio usada o que requiere un SDK o una extensión, como Azure SDK para .NET.

Muchos activos ampliamente utilizados se comportan de la misma manera en Visual Studio 2015, Visual Studio 2013 y las dos versiones anteriores. Por ejemplo, en Visual Studio 2015, puede abrir un proyecto creado en Visual Studio 2013 o Visual Studio 2012, cambiarlo y, a continuación, volver a abrirlo en Visual Studio 2015. Los cambios se conservan y el proyecto se comporta igual que en la versión anterior. Esto mismo sucede con muchos activos creados en Visual Studio 2010 SP1.

Para Visual Basic, Visual Studio 2015 no presentó ningún cambio que impida que una aplicación de Visual Basic creada en Visual Studio 2013 se compile. El comportamiento en el entorno de ejecución de las aplicaciones de Visual Basic que se vuelven a compilar con Visual Studio 2015 no cambiará.

Si utiliza Visual Studio 2015 junto con Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1, puede crear y modificar proyectos y archivos en cualquiera de estas versiones. Puede transferir proyectos y archivos entre las versiones siempre y cuando no agregue características que no se admitan en una o varias versiones.

## <a name="project"></a> Proyectos

En la lista siguiente se describe la compatibilidad en Visual Studio 2015 y Visual Studio 2013 para los proyectos que se crearon en Visual Studio 2012 o Visual Studio 2010 SP1. Use esta lista para ayudar a determinar si puede abrir un proyecto "tal cual" en Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1, o si tiene que modificarlo para garantizar la compatibilidad.

|Tipo de proyecto|Compatibilidad|
|---------------------|-------------------|
|Aplicaciones de la Plataforma universal de Windows|Para instalar las herramientas de las aplicaciones universales de Windows, en el programa de instalación de Visual Studio, seleccione **Personalizado** o **Modificar**; luego, seleccione **Herramientas de desarrollo de aplicaciones universales de Windows**.<br /><br /> El desarrollo de aplicaciones de la Plataforma universal de Windows (UWP) para Windows 10 solo se admite en Visual Studio 2015 en Windows 10 o en [!INCLUDE[win81](../includes/win81-md.md)].|
|Aplicaciones de la Tienda Windows|El desarrollo de aplicaciones de la Tienda Windows, incluidas las aplicaciones universales destinadas a Windows 8.1 y Windows Phone 8.1, puede llevarse a cabo en [!INCLUDE[win81](../includes/win81-md.md)] y 10 de Windows. Los proyectos de [!INCLUDE[win8](../includes/win8-md.md)] existentes se pueden seguir atendiendo, pero no se pueden crear nuevos proyectos de [!INCLUDE[win8](../includes/win8-md.md)] . Los proyectos de [!INCLUDE[win81](../includes/win81-md.md)] pueden depender únicamente de determinados tipos de referencias. Para más información, vea [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md). **Nota:** los proyectos de [!INCLUDE[win81](../includes/win81-md.md)] creados con Visual Studio 2015 o Visual Studio 2013 no se pueden abrir en Visual Studio 2012. Esto se debe a que los proyectos de [!INCLUDE[win81](../includes/win81-md.md)] creados con Visual Studio 2015 y Visual Studio 2013 tienen esas versiones como destino, y Visual Studio 2012 solo admite proyectos de [!INCLUDE[win8](../includes/win8-md.md)] que tengan como destino [!INCLUDE[win8](../includes/win8-md.md)].|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Puede crear y utilizar estos proyectos en Visual Studio 2015 y Visual Studio 2013 después de instalar el paquete adecuado de compatibilidad con múltiples versiones. Estos proyectos no se admiten en Visual Studio 2010 SP1.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Puede crear y abrir estos proyectos en Visual Studio 2015, Visual Studio 2013 y Visual Studio 2012, pero no en Visual Studio 2010 SP1.|
|BizTalk|Los proyectos de BizTalk Server no son compatibles con Visual Studio 2015 o Visual Studio 2013.|
|Aplicación o biblioteca de clases de Silverlight 4 de C#/Visual Basic|Si permite que Visual Studio actualice el proyecto automáticamente, puede abrirlo en Visual Studio 2013 o Visual Studio 2012.|
|Webform o Windows Forms de C#/Visual Basic|Puede abrir el proyecto en Visual Studio 2013 y Visual Studio 2012.|
|Visual Basic 6 y Visual C++ 6|Visual Studio 2012 y Visual Studio 2013 no admiten la depuración de aplicaciones compiladas con Visual Basic 6 o Visual C++ 6; para depurar estas aplicaciones, debe usar versiones anteriores de Visual Studio.|
|Prueba de IU codificada|Si permite que Visual Studio actualice el proyecto automáticamente, puede abrirlo en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1.|
|F#|Si permite que Visual Studio actualice un proyecto creado en Visual Studio 2010 SP1, puede abrirlo en Visual Studio 2013 y Visual Studio 2012. Sin embargo, no puede actualizar un proyecto de Silverlight creado en una versión de Visual Studio anterior a Visual Studio 2013. En su lugar, debe crear un proyecto de Silverlight en Visual Studio 2013 y, a continuación, copiar el código en él. Los proyectos de Silverlight creados en Visual Studio 2013 tienen como destino Silverlight 5.|
|LightSwitch|Si permite que Visual Studio actualice el proyecto automáticamente, solo puede abrirlo en Visual Studio 2013.|
|Caché de base de datos local|La plantilla Caché de base de datos local y el cuadro de diálogo **Configurar sincronización de datos** no se incluyen en Visual Studio 2013. Puede usar Visual Studio 2013 para abrir y ejecutar proyectos creados en [!INCLUDE[vs2010](../includes/vs2010-md.md)] si está instalado Microsoft Synchronization Services v1.0, pero si desea actualizarlos en Visual Studio 2013, debe realizar todos los cambios manualmente en el código. Como alternativa, puede seguir utilizando [!INCLUDE[vs2010](../includes/vs2010-md.md)] para mantener y actualizar estos proyectos.  En el caso de desarrollos nuevos, debe tener como destino el nuevo modelo de sincronización que proporciona Microsoft Sync Framework. Para obtener más información, vea [Centro para desarrolladores de Microsoft Sync Framework](https://msdn.microsoft.com/sync/default).|
|Marco de trabajo Model-View-Controller|Visual Studio 2010 SP1 solo admite MVC 2 y MVC 3, Visual Studio 2012 solo admite MVC 3 y MVC 4, y Visual Studio 2013 solo admite MVC 4. Para obtener información sobre cómo actualizar automáticamente MVC 2 a MCV 3, vea [Actualizador de aplicaciones ASP.NET MVC 3](https://aspnet.codeplex.com/releases/view/59008). Para obtener información acerca de cómo actualizar manualmente MVC 2 a MVC 3, vea [Herramientas para actualizar un proyecto ASP.NET MVC 2 a ASP.NET MVC 3](https://aspnet.codeplex.com/releases/view/59008). Para obtener información acerca de cómo actualizar manualmente MVC 3 a MVC 4, vea [Actualizar un proyecto ASP.NET MVC 3 a ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes). Si el proyecto tiene como destino .NET Framework 3.5 SP1, debe redestinarlo para que utilice .NET Framework 4.|
|Modelado|Si permite que Visual Studio actualice el proyecto automáticamente, puede abrirlo en Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1.<br /><br /> Cuando Team Foundation compila un proyecto de modelado, intenta validar las capas del proyecto. En Visual Studio 2013, Team Foundation Build no puede validar las capas de un proyecto de modelado creado en Visual Studio 2010 SP1. Sin embargo, en Visual Studio 2010 SP1, Team Foundation Build puede validar las capas de un proyecto de modelado creado en Visual Studio 2013.|
|Depurador de clúster MPI|Si está instalada la misma versión del entorno de ejecución o de las herramientas en los equipos que ejecutan Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1, puede abrir este proyecto en las tres versiones.|
|Programa de instalación de MSI (.vdproj)|Este proyecto no se puede abrir en Visual Studio 2013 porque no admite ese tipo de proyecto. Se recomienda usar InstallShield Limited Edition para Visual Studio (ISLE), una solución de implementación gratuita que admite directamente la mayoría de las plataformas y los runtimes de aplicación de Windows. También puede usar ISLE para importar datos y configuraciones de proyectos del instalador de Visual Studio. .|
|Office 2007 VSTO|Si actualiza el proyecto para que tenga como destino Office 2013 y .NET Framework 4, puede abrir este proyecto en Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1.|
|Office 2010 VSTO|Si el proyecto tiene como destino .NET Framework 4, puede abrirlo en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1. Todos los demás proyectos requieren una actualización unidireccional.|
|Aplicaciones de Internet enriquecidas|Si actualiza el proyecto, puede abrirlo en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1.|
|SharePoint 2007|Este proyecto no se puede abrir en Visual Studio 2013. Sin embargo, si actualiza manualmente el proyecto a SharePoint 2010, puede abrirlo en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1. Para obtener más información sobre cómo actualizar SharePoint 2007, vea [Migrar de SharePoint 2007 a SharePoint 2010 para el profesional de TI](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) y [Herramienta de migración del motor de búsqueda Enterprise Search de SharePoint para SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Puede abrir el proyecto en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1.|
|SketchFlow|Si permite que Visual Studio actualice el proyecto a WPF 4.5/Silverlight 5, puede abrirlo en Visual Studio 2012 y Visual Studio 2013.|
|Base de datos [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]|Puede abrir el proyecto en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1. Si tiene un archivo de base de datos (.mdf) creado en una versión anterior de SQL Server, debe actualizarlo a [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] antes de poder utilizarlo con SQL Server Express LocalDB, pero la base de datos ya no es compatible con versiones anteriores de SQL Server. Si no actualiza, puede seguir trabajando con la base de datos en Visual Studio 2013 mediante la instalación y el uso de [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] en el mismo equipo. Para obtener más información, vea [Actualizar archivos .mdf](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Si [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express está instalado en los equipos que ejecutan Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1, puede abrir el proyecto en las tres versiones.|
|Proyecto de informe de SQL Server|Puede abrir el proyecto en Visual Studio 2013 y Visual Studio 2012. Solo para el modo local (es decir, cuando no esté conectado a SQL Server), no obtendrá la experiencia en tiempo de diseño para los controles asociados al visor de [!INCLUDE[vs2010](../includes/vs2010-md.md)], pero el proyecto funcionará correctamente en tiempo de ejecución. **PRECAUCIÓN:**  Si agrega una característica específica a Visual Studio 2013, el esquema del informe se actualizará automáticamente y ya no podrá abrir el proyecto en Visual Studio 2012.|
|Pruebas unitarias|Puede usar [!INCLUDE[TCMext](../includes/tcmext-md.md)] en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1 para abrir pruebas creadas en cualquiera de estas versiones.|
|Visual C++|Puede usar Visual Studio 2013 para abrir un proyecto de C++ creado en Visual Studio 2012 o Visual Studio 2010 SP1. Si desea utilizar el entorno de compilación de Visual Studio 2013 para compilar un proyecto creado en Visual Studio 2012, debe tener ambas versiones de Visual Studio instaladas en el mismo equipo. Para obtener más información, vea [Cómo: Actualizar proyectos de Visual C++ a Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) y [Guía de migración y actualización de Visual C++](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Web de Visual Studio 2010|Si permite que Visual Studio actualice el proyecto automáticamente, puede abrirlo en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1.|
|Base de datos de Visual Studio 2010 (.dbproj)|Si convierte el proyecto en un proyecto de base de datos de SQL Server Data Tools, puede abrirlo en Visual Studio 2013. Sin embargo, Visual Studio 2013 no admite estos artefactos:<br /><br /> - pruebas unitarias<br />- planes de generación de datos<br />- archivos de comparación de datos<br />- extensiones de regla personalizada para análisis de código estático<br />- server.sqlsettings<br />- archivos .sqlcmd<br />- extensiones de implementación personalizadas<br />- proyectos parciales (.files)<br /><br /> Si instala SQL Server Data Tools, puede abrir el proyecto en Visual Studio 2010 SP1 después de la conversión. Para obtener más información, vea [Herramientas de datos de Microsoft SQL Server](https://msdn.microsoft.com/data/tools.aspx).|
|Visual Studio 2010 Visual Database Tools|Puede abrir este proyecto en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1.|
|Visual Studio Lab Management|Puede usar [!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1 para abrir entornos creados en cualquiera de estas versiones. Sin embargo, la versión de Microsoft Test Manager debe coincidir con la versión de Team Foundation Server para poder crear entornos.|
|Macro de Visual Studio|Este proyecto no se puede abrir en Visual Studio 2013 porque no admite el tipo de proyecto.|
|Visual Studio SDK/VSIX|Después de actualizar un proyecto del SDK de Visual Studio a Visual Studio 2013, no se puede abrir en Visual Studio 2012. Para obtener más información, vea [Cómo: migrar proyectos de extensibilidad a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Microsoft Azure Tools para Visual Studio|Si usa Microsoft Azure Tools para la versión 2.1 de Visual Studio, puede abrir el proyecto en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1. En el caso de los proyectos que tienen como destino versiones anteriores, si permite que Visual Studio actualice el proyecto a la versión 2.1, puede abrirlo en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1.|
|Windows Communication Foundation, Windows Presentation Foundation|Puede abrir este proyecto en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1.|
|Windows Mobile|Este proyecto no se puede abrir en Visual Studio 2013 porque no admite el tipo de proyecto.|
|Windows Phone 7.1|Si permite que Visual Studio actualice el proyecto a Windows Phone 8.0, puede abrirlo en Visual Studio 2012 y Visual Studio 2013.|
|Otros|Puede abrir la mayoría de los demás tipos de proyectos en Visual Studio 2012, Visual Studio 2013 y Visual Studio 2010 SP1.|
|Sitios web de FrontPage|Este proyecto no se puede abrir en Visual Studio 2013 porque no admite el tipo de proyecto.|
|Biblioteca de clases portable|Si permite que Visual Studio actualice el proyecto automáticamente, puede abrirlo en Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1.<br /><br /> - Los proyectos destinados a Silverlight 4 tendrán como destino Silverlight 5.<br />- Los proyectos destinados a Windows Phone 7.0 o Windows Phone 7.5 tendrán como destino Windows Phone 8.<br />- Los proyectos destinados a Xbox 360 ya no tendrán como destino Xbox 360.|
|Proyectos de Azure como los de servicios de nube (extensión .ccproj) y los del Administrador de recursos de Azure (proyectos de implementación de nube) con la extensión .deployproj|Para abrir estos tipos de proyecto, instale primero el [SDK de Azure para .NET](https://azure.microsoft.com/downloads/)y luego abra el proyecto.|

## <a name="troubleshooting-project-compatibility-issues"></a>Solucionar problemas de compatibilidad de proyectos
 Estas son algunas de las cosas que puede hacer cuando un proyecto no se abre en Visual Studio 2015 o Visual Studio 2013:

- Si intenta abrir un proyecto que no es compatible con Visual Studio 2015 o Visual Studio 2013 y para el que no está instalada la versión asociada de Visual Studio, puede aparecer un mensaje que indica que el tipo de proyecto no es compatible y el tipo de proyecto podría aparecer en el cuadro de diálogo **Revisar cambios de proyecto y solución** en **Proyectos no admitidos**. Para resolver este problema, abra la página Programas y características del **Panel de control**de Windows, seleccione **Visual Studio**y elija **Cambiar**, **Reparar**. Después puede instalar la versión que falta.

- Si intenta abrir un proyecto para una aplicación de escritorio en [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)], se produce un error y se muestra uno de estos mensajes: "Esta edición de Visual Studio solo admite aplicaciones [!INCLUDE[win81](../includes/win81-md.md)]" o "Este proyecto no es compatible con la edición actual de Visual Studio". [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] está restringido al desarrollo, prueba e implementación de aplicaciones de la Tienda Windows diseñadas para Windows 8.1. Para abrir un proyecto de aplicación de escritorio, debe usar una edición de Visual Studio que admita ese tipo de proyecto.

   Para obtener más información sobre las ediciones de Visual Studio, vea [Productos de Microsoft Visual Studio](https://visualstudio.microsoft.com/products/).

- Si intenta abrir un proyecto de aplicación de la Tienda Windows en [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop, aparece un error. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop no se puede usar para compilar aplicaciones de la Tienda Windows. Si desea compilar aplicaciones de la Tienda Windows, también puede instalar [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]. O bien, para desarrollar aplicaciones para todas las plataformas de Microsoft y la Web, pruebe Visual Studio Professional 2013.

- Si un proyecto requiere características específicas de Visual Studio 2013, no se puede abrir en una versión anterior.

- Si utiliza Visual Studio 2012 y desea abrir un proyecto creado en Visual Studio 2013, es posible que pueda personalizar el sistema del proyecto para incorporar características de Visual Studio 2013. Para obtener más información sobre cómo hacerlo, vea [Crear proyectos personalizados con identificación de versión](../misc/making-custom-projects-version-aware.md).

  Para obtener información adicional sobre la solución de problemas, vea el artículo de KB sobre [Compatibilidad de Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) .

## <a name="file"></a> Archivos

La lista siguiente identifica si Visual Studio 2013 admite cada tipo de archivo, si puede abrir el archivo en Visual Studio 2012 y Visual Studio 2010 SP1 y si tiene que modificarlo para garantizar la compatibilidad.

|Tipo de archivo|Compatibilidad|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (archivos .xml)|Puede abrir estos archivos en Visual Studio 2012, Visual Studio 2013 y Visual Studio 2010 SP1.|
|Esquemas de archivo sin formato de BizTalk|Puede agregar estos esquemas a un proyecto de BizTalk 2013 en Visual Studio 2013. Para usar Visual Studio 2013 con proyectos de BizTalk 2010 con esquemas de archivo sin formato, instale BizTalk 2013 en el equipo que tiene Visual Studio 2013. La primera vez que abra el proyecto de BizTalk 2010, se actualizará automáticamente al sistema de proyectos de BizTalk 2013 o Visual Studio 2013.|
|Archivos de definición de informe de cliente (.rdlc)|Puede abrir estos archivos en Visual Studio 2013; el esquema se actualizará automáticamente si agrega características y controles de Visual Studio 2013.|
|Conjuntos de reglas de análisis de código|Puede abrir estos archivos en Visual Studio 2012, Visual Studio 2013 y Visual Studio 2010 SP1.|
|Archivos de paquetes de aplicación de capa de datos|Puede abrir estos archivos en Visual Studio 2013 si son la versión 2.0 o la versión 2.5.|
|Archivos de volcado de memoria del depurador|Puede abrir estos archivos en Visual Studio 2012, Visual Studio 2013 y Visual Studio 2010 SP1.|
|Archivos de diagrama de Directed Graph Markup Language (DGML)|Puede abrir estos archivos en Visual Studio 2012, Visual Studio 2013 y Visual Studio 2010 SP1 sin cambiar el archivo.|
|Archivos Entity Data Model (EDMX)|En Visual Studio 2013, puede abrir un archivo EDMX que tenga como destino el .NET Framework 4.5 o .NET Framework 4 sin cambiar el archivo.|
|Archivos de informe del generador de perfiles|Puede abrir los archivos de informe del generador de perfiles (. VSP. VSPs,. psess y. vspf) en Visual Studio 2012 y Visual Studio 2013. No puede abrir un archivo .vspx en Visual Studio 2010 SP1.|
|Archivo de solución (.suo)|Puede usar Visual Studio 2013 para abrir un archivo de solución creado en Visual Studio 2012 o Visual Studio 2010 SP1.|
|SQL Server Compact Edition|Visual Studio 2013 no admite la edición de SQL Server Compact.|
|Archivos SQLX|Para abrir estos archivos en Visual Studio 2013, debe realizar una actualización unidireccional, implementar el archivo. sqlx en la versión de destino de Visual Studio y, a continuación, recompilar el archivo en formato. dacpac.|
|Archivos de registro de IntelliTrace de [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Puede abrir estos archivos en Visual Studio 2012, Visual Studio 2013 y Visual Studio 2010 SP1.|
|Archivos del Analizador de memoria de JavaScript (.diagsession)|Los archivos creados por versiones anteriores de Visual Studio se pueden ver en Visual Studio 2013. Sin embargo, en función de la información recopilada, es posible que los archivos creados en Visual Studio 2013 no se abran en Visual Studio 2012 o Visual Studio 2010 SP1.|

## <a name="integration"></a> Activos de integración

Puede encontrar problemas de compatibilidad si usa clientes y servidores de distintas versiones de Visual Studio Team Foundation Server.

|Tipo de integración|Compatibilidad|
|-------------------------|-------------------|
|Revisión de código y Mi trabajo|Las características Revisión de código y Mi trabajo no funcionarán si conecta un cliente de [!INCLUDE[esprfound](../includes/esprfound-md.md)] a [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)].|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|No puede usar un entorno de 64 bits como MSBuild o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] para compilar aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] creadas en [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)].|

## <a name="see-also"></a>Vea también

- [Crear proyectos personalizados con identificación de versión](../misc/making-custom-projects-version-aware.md)
