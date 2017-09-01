---
title: "Cuadro de diálogo Requisitos previos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 75
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 5a8237e5c437878b22bd3c67a3a4ba2cdc3fa126
ms.contentlocale: es-es
ms.lasthandoff: 05/26/2017

---
# <a name="prerequisites-dialog-box"></a>Prerequisites Dialog Box
Este cuadro de diálogo permite especificar los componentes necesarios que se instalan, cómo se instalan y en qué orden se instalan los paquetes.  
  
 Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos** , haga clic en la pestaña **Publicar** . En la página **Publicar**, haga clic en **Requisitos previos**. Para los proyectos de programas de instalación, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se abra el cuadro de diálogo **Páginas de propiedades**, haga clic en **Requisitos previos**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|**Crear programa de instalación para instalar los componentes necesarios**|Incluye los componentes necesarios del programa de instalación de la aplicación (Setup.exe) para que se instalen antes que esta, en orden de dependencia. Esta opción se encuentra activada de forma predeterminada. Si no se selecciona, no se crea ningún archivo Setup.exe.|  
|**Elegir los requisitos previos que se van a instalar**|Especifica si se deben instalar componentes como [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], Crystal Reports, etc.<br /><br /> Por ejemplo, al activar la casilla situada junto a **SQL Server 2005 Express Edition SP2**, se indica al programa de instalación que debe comprobar si este componente está instalado en el equipo de destino y, si no lo está, debe instalarlo.<br /><br /> Para obtener información detallada sobre los paquetes de requisitos previos, vea la tabla de Información de requisitos más adelante en este tema.|  
|**Buscar más componentes redistribuibles en Microsoft Update**|Este vínculo le llevará al sitio web de [paquetes de programa previo adicionales para redistribuir componentes](http://go.microsoft.com/fwlink/?LinkId=208835) para comprobar si hay actualizaciones.|  
|**Descargar los requisitos previos del sitio web del proveedor de los componentes**|Especifica que los componentes necesarios se instalarán desde el sitio web del proveedor. Ésta es la opción predeterminada.|  
|**Descargar los requisitos previos de la misma ubicación que mi aplicación**|Especifica que los componentes necesarios se instalarán desde la misma ubicación que la aplicación. Mediante esta acción, se copian todos los paquetes de requisitos previos a la ubicación de publicación. Para que esta opción funcione, los paquetes se deben encontrar en el equipo de desarrollo.|  
|**Descargar los requisitos previos de la siguiente ubicación**|Especifica que los componentes de requisitos previos se instalarán desde la ubicación seleccionada. Puede usar el botón **Examinar** para seleccionar una ubicación.|  
  
## <a name="prerequisites-information"></a>Información de requisitos previos  
 Los componentes de requisitos previos que aparecen en el cuadro de diálogo **Requisitos previos** pueden ser diferentes a los que figuran en la lista siguiente. Los paquetes de requisitos previos incluidos en el **cuadro de diálogo Requisitos previos** se establecen automáticamente la primera vez que abre el cuadro de diálogo. Si posteriormente cambia la plataforma de destino del proyecto, deberá seleccionar manualmente los requisitos previos para que coincidan con la nueva plataforma de destino.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|**.NET Framework 3.5 SP1**|Este paquete instala lo siguiente:<br /><br /> -   Versiones de .NET Framework 2.0, 3.0 y 3.5.<br />-   Compatibilidad con todas las versiones de .NET Framework en sistemas operativos de 32 bits (x86) y de 64 bits (x64).<br />-   Paquetes de idiomas para cada versión de .NET Framework que se instala con el paquete.<br />-   Service Pack para .NET Framework 2.0 y 3.0.<br /><br /> .NET Framework 3.0 se incluye con Windows Vista y .NET Framework 3.5 se incluye con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se requiere .NET Framework 3.5 para todos los proyectos de Visual Basic y Visual C# que se compilen para los sistemas operativos de 32 bits y cuya plataforma de destino esté establecida en **.NET Framework 3.5**, así como para los proyectos de Visual Basic y Visual C# compilados para sistemas operativos de 64 bits. (No se admite IA64.) Tenga en cuenta que, de manera predeterminada, los proyectos de Visual Basic y Visual C# se compilan para cualquier arquitectura de CPU. Para obtener más información, consulte [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Redistribuir .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) e [Implementar requisitos previos de aplicaciones de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Este elemento está seleccionado de manera predeterminada.|  
|**.NET Framework 3.5 SP1 Client Profile**|.NET Framework Client Profile es un subconjunto de la versión completa de .NET Framework 3.5 SP1 destinado a aplicaciones cliente. Proporciona un subconjunto simplificado de las características de Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) y ClickOnce. Esto permite habilitar escenarios de implementación rápida para WPF, Windows Forms, WCF y las aplicaciones de consola que tienen como destino .NET Framework Client Profile. Para obtener más información, consulte [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).|  
|**Microsoft .NET Framework 4 (x86 y x64)**|Este paquete instala .NET Framework 4 para las plataformas x86 y x64.<br /><br /> Para obtener más información, consulte [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Redistribuir .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) e [Implementar requisitos previos de aplicaciones de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Este elemento está seleccionado de manera predeterminada.|  
|**Microsoft .NET Framework 4 Client Profile (x86 y x64)**|.NET Framework 4 Client Profile es un subconjunto de la versión completa de .NET Framework 4 destinada a aplicaciones cliente. Proporciona un subconjunto simplificado de las características de Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) y ClickOnce. Esto permite habilitar escenarios de implementación rápida para WPF, Windows Forms y las aplicaciones de consola que tienen como destino .NET Framework 4 Client Profile. Para obtener más información, consulte [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).|  
|**Ensamblados de interoperabilidad primarios de Microsoft Office 2007**|Este paquete instala los ensamblados de interoperabilidad primarios para productos de Microsoft Office 2007. Los ensamblados de interoperabilidad primarios permiten que el código administrado interactúe con el modelo de objetos basado en COM de una aplicación de Microsoft Office. Para obtener más información, consulte [Ensamblados de interoperabilidad primarios de Office](/office-dev/office-dev/office-primary-interop-assemblies).|  
|**Microsoft Visual Basic PowerPacks versión 10.0**|Los Power Packs son complementos, controles, componentes y herramientas que ayudan a desarrollar aplicaciones de Visual Basic. Esta versión contiene el componente <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>, que permite imprimir el contenido de un Windows Form, y la biblioteca de compatibilidad de impresoras, que permite ejecutar el código de impresora de Visual Basic 6.0 sin modificarlo.|  
|**Microsoft Visual F# Runtime for .NET 2.0**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual F# para los sistemas operativos x64 y x86, que proporcionan compatibilidad con la programación funcional así como con la programación tradicional orientada a objetos e imperativa (de procedimientos). Se debe instalar este paquete si la aplicación o sus componentes se crearon en Visual F# y en .NET Framework 2.0, .NET Framework 3.0 o .NET Framework 3.5.<br /><br /> Para obtener más información, consulte [Referencia del lenguaje F#](http://msdn.microsoft.com/Library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual F# Runtime for .NET 4.0**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual F# para los sistemas operativos x64 y x86, que proporcionan compatibilidad con la programación funcional así como con la programación tradicional orientada a objetos e imperativa (de procedimientos). Se debe instalar este paquete si la aplicación o sus componentes se crearon en Visual F# y en .NET Framework 4.<br /><br /> Para obtener más información, consulte [Referencia del lenguaje F#](http://msdn.microsoft.com/Library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Visor de informes de Microsoft Visual Studio 2010**|Este paquete instala nuevos controles del Visor de informes que se pueden utilizar para agregar informes de datos enriquecidos a Windows Forms y a las aplicaciones ASP.NET.|  
|**Microsoft Visual Studio 2010 para Office Runtime (x86 y x64)**|Office Developer Tools para Visual Studio proporcionan herramientas integradas fáciles de usar para la creación de soluciones empresariales personalizadas con Microsoft Office. Puede crear soluciones de cliente administradas e inteligentes que utilicen las aplicaciones de Office como interfaz de usuario. Las herramientas permiten a los desarrolladores crear soluciones seguras que resulten fáciles de implementar y mantener.<br /><br /> Para obtener más información, consulte [Cómo: Publicar una solución de Office usando ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|  
|**SQL Server 2005 Express Edition SP2 (x86)**|Este paquete instala Microsoft SQL Server 2005 Express Edition SP2, una aplicación de base de datos que se basa en [!INCLUDE[sqprsqext](../../ide/reference/includes/sqprsqext_md.md)]. SQL Server Express sustituye a Microsoft SQL Server Desktop Engine (MSDE). SQL Server Express es gratuito, se puede redistribuir (sujeto a un contrato de licencia) y funciona como base de datos cliente y como base de datos de servidor básica. Incluye las mismas características que SQL Server 2005, a excepción de las siguientes:<br /><br /> -   No admite ninguna característica empresarial.<br />-   Se limita a una CPU.<br />-   Límite de memoria de 1 gigabyte (GB) para el grupo de búferes.<br />-   4 GB de tamaño máximo para las bases de datos.|  
|**SQL Server 2008 Express**|Este paquete instala Microsoft SQL Server 2008 Express, una edición gratuita de Microsoft SQL Server 2008, que representa la base de datos ideal para aplicaciones web pequeñas, de servidor o de escritorio. Se puede utilizar de forma gratuita para el desarrollo y producción. Es necesario [registrarse](http://go.microsoft.com/fwlink/?LinkId=130380) de manera gratuita para distribuir SQL Server 2008 Express con la aplicación.<br /><br /> El comportamiento del arranque es el siguiente:<br /><br /> -   Si el equipo ya tiene instalado SQL Server 2008 Express o una versión posterior, se mantiene SQL Server 2008 Express o las versiones posteriores.<br />-   Si el equipo no tiene instalada ninguna versión de SQL Server 2008 Express o posterior, el paquete instala la última versión de SQL Server 2008 Express SP1.<br /><br /> Para obtener más información sobre SQL Server 2008 Express, visite [http://go.microsoft.com/fwlink/?LinkId=183586](http://go.microsoft.com/fwlink/?LinkId=183586).|  
|**Bibliotecas en tiempo de ejecución de Visual C++ 2010 (IA64)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para la arquitectura Itanium, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|  
|**Bibliotecas en tiempo de ejecución de Visual C++ 2010 (x64)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para los sistemas operativos x64, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|  
|**Bibliotecas en tiempo de ejecución de Visual C++ 2010 (x86)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para los sistemas operativos x86, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|  
|**Windows Installer 3.1**|Este paquete instala la versión 3.1 redistribuible de Microsoft Windows Installer, que permite instalar proyectos de instalación de Windows Installer. Viene preinstalado en el SP1 de Windows Server 2003 y posterior.<br /><br /> Este elemento está seleccionado de manera predeterminada.|  
|**Windows Installer 4.5**|Este paquete instala la versión 4.5 redistribuible de Microsoft Windows Installer, que permite instalar proyectos de instalación de Windows Installer.|  
  
## <a name="see-also"></a>Vea también  
 [Panel Publicar, Diseñador de proyectos](../../ide/reference/publish-page-project-designer.md)   
 [Requisitos previos para la implementación de aplicaciones](../../deployment/application-deployment-prerequisites.md)   
 [Redistribuir .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287)   
 [Implementar requisitos previos de aplicaciones de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md)   
 [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)
