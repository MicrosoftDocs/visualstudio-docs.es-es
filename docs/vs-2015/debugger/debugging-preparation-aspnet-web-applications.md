---
title: 'Preparación de la depuración: aplicaciones Web de ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691457"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Preparación de la depuración: aplicaciones Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] plantilla de sitio Web crea una aplicación de formulario Web Forms. Cuando se crea un sitio Web usando esta plantilla, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea la configuración predeterminada para la depuración. En el cuadro de diálogo **propiedades del proyecto** , puede especificar si desea que la página web sea una página de inicio. Cuando se inicia la depuración [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] de un sitio web con estos valores predeterminados, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] inicia Internet Explorer y asocia el depurador al [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proceso de trabajo (aspnet_wp.exe o w3wp.exe). Para obtener más información, vea [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Para crear una aplicación de formularios Web Forms  
  
1. En el menú **archivo** , elija **nuevo sitio web**.  
  
2. En el cuadro de diálogo **nuevo sitio web** , seleccione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **sitio web**.  
  
3. Haga clic en **OK**.  
  
### <a name="to-debug-your-web-form"></a>Para depurar el formulario Web Forms  
  
1. Establezca uno o varios puntos de interrupción en los controladores de funciones y eventos.  
  
     Para obtener más información, consulta [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Cuando se alcance un punto de interrupción, ejecute paso a paso el código en la función. Fíjese en la ejecución del código hasta que aísle el problema.  
  
     Para obtener más información, vea [ejecutar paso a paso](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) y [depurar aplicaciones web y scripts](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Cambiar las configuraciones predeterminadas  
 Si desea cambiar las configuraciones predeterminadas Debug y Release creadas por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede hacerlo. Para obtener más información, vea [Cómo: Establecimiento de configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Para cambiar la configuración Debug predeterminada  
  
1. En **Explorador de soluciones**, haga clic con el botón secundario en el sitio web y seleccione **páginas de propiedades** para abrir el cuadro de diálogo **páginas de propiedades** .  
  
2. Haga clic en **Opciones de inicio**.  
  
3. Establezca **acción de inicio** en la página web que se debe mostrar en primer lugar.  
  
4. En **depuradores**, asegúrese de que la opción **depuración de ASP.net** está seleccionada.  
  
     Para obtener más información, vea [configuración de páginas de propiedades para proyectos web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Consulte también  
 [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)
