---
title: 'Preparación de la depuración: Las aplicaciones Web ASP.NET | Microsoft Docs'
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
ms.openlocfilehash: baa5e454eec00c2530190834974cd946838a0947
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996499"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Preparación de la depuración: Aplicaciones Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]plantilla de sitio Web crea una aplicación de formulario Web Forms. Cuando se crea un sitio Web usando esta plantilla, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea la configuración predeterminada para la depuración. En el **las propiedades del proyecto** cuadro de diálogo, puede especificar si desea que la página Web sea una página de inicio. Al comenzar la depuración una [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]sitio Web con estos valores predeterminados, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] inicia Internet Explorer y asocia el depurador a la [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] el proceso de trabajo (aspnet_wp.exe o w3wp.exe). Para obtener más información, consulte [requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Para crear una aplicación de formularios Web Forms  
  
1.  En el **archivo** menú, elija **nuevo sitio Web**.  
  
2.  En el **nuevo sitio Web** cuadro de diálogo, seleccione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **sitio Web**.  
  
3.  Haga clic en **Aceptar**.  
  
### <a name="to-debug-your-web-form"></a>Para depurar el formulario Web Forms  
  
1.  Establezca uno o varios puntos de interrupción en los controladores de funciones y eventos.  
  
     Para obtener más información, consulta [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Cuando se alcance un punto de interrupción, ejecute paso a paso el código en la función. Fíjese en la ejecución del código hasta que aísle el problema.  
  
     Para obtener más información, consulte [ejecución paso a paso](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) y [depurar aplicaciones Web y en Script](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Cambiar las configuraciones predeterminadas  
 Si desea cambiar las configuraciones predeterminadas Debug y Release creadas por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede hacerlo. Para obtener más información, vea [Cómo: Establecimiento de configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Para cambiar la configuración Debug predeterminada  
  
1.  En **el Explorador de soluciones**, haga clic en el sitio Web y seleccione **páginas de propiedades** para abrir el **páginas de propiedades** cuadro de diálogo.  
  
2.  Haga clic en **opciones de inicio**.  
  
3.  Establecer **acción de inicio** a la página Web que se debe mostrar en primer lugar.  
  
4.  En **depuradores**, asegúrese de que **depuración ASP.NET** está seleccionada.  
  
     Para obtener más información, consulte [configuración de las páginas de propiedades para proyectos Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)
