---
title: Cuadro de diálogo Requisitos previos
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37400624d81c533e6ecddb9d6278b5b372410525
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="prerequisites-dialog-box"></a>Cuadro de diálogo Requisitos previos

Este cuadro de diálogo permite especificar los componentes necesarios que se instalan, cómo se instalan y en qué orden se instalan los paquetes.

Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos** , haga clic en la pestaña **Publicar** . En la página **Publicar**, haga clic en **Requisitos previos**. Para los proyectos de programas de instalación, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se abra el cuadro de diálogo **Páginas de propiedades**, haga clic en **Requisitos previos**.

## <a name="uielement-list"></a>Lista de UIElement

|Elemento|Description|
|-------------|-----------------|
|**Crear programa de instalación para instalar los componentes necesarios**|Incluye los componentes necesarios del programa de instalación de la aplicación (Setup.exe) para que se instalen antes que esta, en orden de dependencia. Esta opción se encuentra activada de forma predeterminada. Si no se selecciona, no se crea ningún archivo Setup.exe.|
|**Elegir los requisitos previos que se van a instalar**|Especifica si se deben instalar componentes como [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], Crystal Reports, etc.<br /><br /> Por ejemplo, al activar la casilla situada junto a **SQL Server 2005 Express Edition SP2**, se indica al programa de instalación que debe comprobar si este componente está instalado en el equipo de destino y, si no lo está, debe instalarlo.<br /><br /> Para obtener información detallada sobre los paquetes de requisitos previos, vea la tabla de Información de requisitos más adelante en este tema.|
|**Buscar más componentes redistribuibles en Microsoft Update**|Este vínculo le llevará al sitio web de [paquetes de programa previo adicionales para redistribuir componentes](http://go.microsoft.com/fwlink/?LinkId=208835) para comprobar si hay actualizaciones.|
|**Descargar los requisitos previos del sitio web del proveedor de los componentes**|Especifica que los componentes necesarios se instalarán desde el sitio web del proveedor. Ésta es la opción predeterminada.|
|**Descargar los requisitos previos de la misma ubicación que mi aplicación**|Especifica que los componentes necesarios se instalarán desde la misma ubicación que la aplicación. Mediante esta acción, se copian todos los paquetes de requisitos previos a la ubicación de publicación. Para que esta opción funcione, los paquetes se deben encontrar en el equipo de desarrollo.|
|**Descargar los requisitos previos de la siguiente ubicación**|Especifica que los componentes de requisitos previos se instalarán desde la ubicación seleccionada. Puede usar el botón **Examinar** para seleccionar una ubicación.|

## <a name="prerequisites-information"></a>Información de requisitos previos

Los componentes de requisitos previos que aparecen en el cuadro de diálogo **Requisitos previos** pueden ser diferentes a los que figuran en la lista siguiente. Los paquetes de requisitos previos incluidos en el **cuadro de diálogo Requisitos previos** se establecen automáticamente la primera vez que abre el cuadro de diálogo. Si posteriormente cambia la plataforma de destino del proyecto, deberá seleccionar manualmente los requisitos previos para que coincidan con la nueva plataforma de destino.

|Elemento|Description|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Este paquete instala lo siguiente:<br /><br /> -   Versiones de .NET Framework 2.0, 3.0 y 3.5.<br />-   Compatibilidad con todas las versiones de .NET Framework en sistemas operativos de 32 bits (x86) y de 64 bits (x64).<br />-   Paquetes de idiomas para cada versión de .NET Framework que se instala con el paquete.<br />-   Service Pack para .NET Framework 2.0 y 3.0.<br /><br /> .NET Framework 3.0 se incluye con Windows Vista y .NET Framework 3.5 se incluye con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se requiere .NET Framework 3.5 para todos los proyectos de Visual Basic y C# que se compilen para los sistemas operativos de 32 bits y cuya plataforma de destino esté establecida en **.NET Framework 3.5**, así como para los proyectos de Visual Basic y C# compilados para sistemas operativos de 64 bits. (No se admite IA64.) Tenga en cuenta que, de manera predeterminada, los proyectos de Visual Basic y C# se compilan para cualquier arquitectura de CPU. Para obtener más información, consulte [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md) e [Implementar requisitos previos de aplicaciones de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Este elemento está seleccionado de manera predeterminada.|
|**Microsoft .NET Framework 4.x**|Este paquete instala .NET Framework 4.x para las plataformas x86 y x64.|
|**Microsoft System CLR Types para SQL Server 2014 (x64 y x86)**|Este paquete instala Microsoft System CLR Types para SQL Server 2014, tanto x64 como x86.|
|**SQL Server 2008 R2 Express**|Este paquete instala Microsoft SQL Server 2008 R2 Express, una edición gratuita de Microsoft SQL Server 2008 R2, que representa la base de datos ideal para aplicaciones web pequeñas, de servidor o de escritorio. Se puede utilizar de forma gratuita para el desarrollo y producción.|
|**SQL Server 2012 Express**|Este paquete instala Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Este paquete instala Microsoft SQL Server 2012 Express LocalDB.|
|**Bibliotecas en tiempo de ejecución de Visual C++ "14" (ARM)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para la arquitectura Itanium, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliotecas en tiempo de ejecución de Visual C++ "14" (x64)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para los sistemas operativos x64, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliotecas en tiempo de ejecución de Visual C++ "14" (x86)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para los sistemas operativos x86, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Vea también

- [Panel Publicar, Diseñador de proyectos](../../ide/reference/publish-page-project-designer.md)
- [Requisitos previos para la implementación de aplicaciones](../../deployment/application-deployment-prerequisites.md)
- [Implementar requisitos previos de aplicaciones de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)
