---
title: Cuadro de diálogo Requisitos previos
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ecbba1a1c5e8670fd9adcafdfed8cec21dd3912
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567910"
---
# <a name="prerequisites-dialog-box"></a>Cuadro de diálogo Requisitos previos

El cuadro de diálogo **Requisitos previos** permite especificar los componentes necesarios que se instalan, cómo se instalan y en qué orden se instalan los paquetes.

![Cuadro de diálogo Requisitos previos en Visual Studio](media/prerequisites-dialog-box.png)

Para acceder al cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y, luego, seleccione **Proyecto** > **Propiedades**. Cuando aparezca el **Diseñador de proyectos**, seleccione la pestaña **Publicar** y después seleccione **Requisitos previos**. Para los proyectos de programas de instalación, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se abra el cuadro de diálogo **Páginas de propiedades**, haga clic en **Requisitos previos**.

## <a name="uielement-list"></a>Lista de UIElement

|Elemento|Descripción|
|-------------|-----------------|
|**Crear programa de instalación para instalar los componentes necesarios**|Incluye los componentes necesarios del programa de instalación de la aplicación (*Setup.exe*) para que se instalen antes que esta, en orden de dependencia. Esta opción se encuentra activada de forma predeterminada. Si no se selecciona, no se crea ningún archivo *Setup.exe*.|
|**Elegir los requisitos previos que se van a instalar**|Especifica si se pueden instalar los componentes, como las bibliotecas en tiempo de ejecución de .NET Framework y C++.<br /><br />Por ejemplo, al activar la casilla situada junto a **SQL Server 2012 Express**, se indica al programa de instalación que debe comprobar si este componente está instalado en el equipo de destino y, si no lo está, debe instalarlo.<br /><br />Para obtener información detallada sobre los paquetes de requisitos previos, vea la [Información de requisitos previos](#prerequisites-information).|
|**Descargar los requisitos previos del sitio web del proveedor de los componentes**|Especifica que los componentes necesarios se instalarán desde el sitio web del proveedor. Ésta es la opción predeterminada.|
|**Descargar los requisitos previos de la misma ubicación que mi aplicación**|Especifica que los componentes necesarios se instalarán desde la misma ubicación que la aplicación. Mediante esta acción, se copian todos los paquetes de requisitos previos a la ubicación de publicación. Para que esta opción funcione, los paquetes se deben encontrar en el equipo de desarrollo.|
|**Descargar los requisitos previos de la siguiente ubicación**|Especifica que los componentes de requisitos previos se instalarán desde la ubicación introducida. Puede usar el botón **Examinar** para seleccionar una ubicación.|

> [!NOTE]
> Para información sobre dónde colocar los requisitos previos, consulte [Crear paquetes de programa previo](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Información de requisitos previos

Los componentes de requisitos previos que aparecen en el cuadro de diálogo **Requisitos previos** pueden ser diferentes a los que figuran en la lista siguiente. Los paquetes de requisitos previos incluidos en el **cuadro de diálogo Requisitos previos** se establecen automáticamente la primera vez que abre el cuadro de diálogo. Si posteriormente cambia la plataforma de destino del proyecto, debe seleccionar manualmente los requisitos previos para que coincidan con la nueva plataforma de destino.

|Elemento|Descripción|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Este paquete instala lo siguiente:<br /><br /> -   Versiones de .NET Framework 2.0, 3.0 y 3.5.<br />-   Compatibilidad con todas las versiones de .NET Framework en sistemas operativos de 32 bits (x86) y de 64 bits (x64).<br />-   Paquetes de idiomas para cada versión de .NET Framework que se instala con el paquete.<br />-   Service Pack para .NET Framework 2.0 y 3.0.<br /><br /> .NET Framework 3.0 se incluye con Windows Vista y .NET Framework 3.5 se incluye con Visual Studio. Se requiere .NET Framework 3.5 para todos los proyectos de Visual Basic y C# que se compilen para los sistemas operativos de 32 bits y cuya plataforma de destino esté establecida en **.NET Framework 3.5**, así como para los proyectos de Visual Basic y C# compilados para sistemas operativos de 64 bits. (No se admite IA64.) Tenga en cuenta que, de manera predeterminada, los proyectos de Visual Basic y C# se compilan para cualquier arquitectura de CPU. Para obtener más información, vea [Información general sobre destinos de Framework](../../ide/visual-studio-multi-targeting-overview.md) e [Implementación de requisitos previos de aplicaciones de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Este paquete instala .NET Framework 4.x para las plataformas x86 y x64.|
|**Microsoft System CLR Types para SQL Server 2014 (x64 y x86)**|Este paquete instala Microsoft System CLR Types para SQL Server 2014, tanto x64 como x86.|
|**SQL Server 2008 R2 Express**|Este paquete instala Microsoft SQL Server 2008 R2 Express, una edición gratuita de Microsoft SQL Server 2008 R2, que representa la base de datos ideal para aplicaciones web pequeñas, de servidor o de escritorio. Se puede utilizar de forma gratuita para el desarrollo y producción.|
|**SQL Server 2012 Express**|Este paquete instala Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Este paquete instala Microsoft SQL Server 2012 Express LocalDB.|
|**Bibliotecas en tiempo de ejecución de Visual C++ "14" (ARM)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para la arquitectura Itanium, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliotecas en tiempo de ejecución de Visual C++ "14" (x64)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para los sistemas operativos x64, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliotecas en tiempo de ejecución de Visual C++ "14" (x86)**|Este paquete instala las bibliotecas en tiempo de ejecución de Visual C++ para los sistemas operativos x86, que proporcionan las rutinas para programar el sistema operativo Microsoft Windows. Estas rutinas automatizan muchas tareas de programación habituales que no proporcionan los lenguajes C y C++.<br /><br /> Para obtener más información, consulte [Referencia de la biblioteca en tiempo de ejecución de C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Vea también

- [Panel Publicar, Diseñador de proyectos](../../ide/reference/publish-page-project-designer.md)
- [Requisitos previos para la implementación de aplicaciones](../../deployment/application-deployment-prerequisites.md)
- [Implementar requisitos previos de aplicaciones de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Información general sobre destinos de Framework](../../ide/visual-studio-multi-targeting-overview.md)
