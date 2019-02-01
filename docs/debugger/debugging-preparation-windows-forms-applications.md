---
title: Prepararse para depurar las aplicaciones de Windows Forms | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0033bb762a42090bd1849d6acc609cf248b28179
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931978"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Preparación de la depuración: Aplicaciones de Windows Forms
La plantilla de proyecto de Windows Forms crea una aplicación de Windows Forms. La depuración de este tipo de aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es muy sencilla. Para obtener más información, consulte [crear un proyecto de aplicación Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).  
  
 Cuando se crea un proyecto de formularios Windows Forms con la plantilla de proyecto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente la configuración requerida para las versiones Debug y Release. Si fuera necesario, puede cambiar esta configuración. Esta configuración se puede cambiar en el cuadro de diálogo **\<Páginas de propiedades de <nombre de proyecto>** (**Mi proyecto** en Visual Basic).  
  
 Para obtener más información, consulte [configuración recomendada de propiedad](../debugger/managed-debugging-recommended-property-settings.md).  
  
 En la tabla siguiente se muestra una configuración de propiedades adicional recomendada.  
  
### <a name="configuration-properties-in-debug-tab"></a>Propiedades de configuración de la ficha Depurar  
  
|**Nombre de la propiedad**|**Configuración**|  
|-----------------------|-----------------|  
|**Acción de inicio**|- Establézcala en **Proyecto de inicio** en la mayoría de los casos. Establézcala en **Programa externo de inicio** para iniciar otro ejecutable al comenzar la depuración (normalmente para la depuración de archivos DLL).|  
  
 Es posible depurar aplicaciones de Windows Forms dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o mediante la asociación a una aplicación que ya está en ejecución. Para obtener más información acerca de cómo adjuntar, vea [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Para depurar una aplicación de Windows Forms en C#, F# o Visual Basic  
  
1. Abra el proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2. Cree puntos de interrupción según sea necesario.  
  
    Debido a que las aplicaciones de Windows Forms están orientadas a eventos, los puntos de interrupción entrarán en el código del controlador de eventos o en métodos llamados por el código del controlador de eventos. Entre los eventos típicos en los cuales colocar puntos de interrupción se encuentran:  
  
   1. Eventos asociados a un control, como Click, Enter, etc.  
  
   2. Eventos asociados al inicio y apagado de una aplicación como Load, Activated, etc.  
  
   3. Eventos de foco y validación.  
  
      Para más información, consulte el artículo sobre [creación de controladores de eventos en Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).  
  
3. En el menú **Depurar**, haga clic en **Iniciar**.  
  
4. Depurar con las técnicas descritas en [primero analicemos el depurador](../debugger/debugger-feature-tour.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Cómo: establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](/dotnet/framework/winforms/index)