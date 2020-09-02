---
title: 'Preparación de la depuración: aplicaciones de Windows Forms | Microsoft Docs'
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
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b11855fbd19dc464f92b4339684ef8346556c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691149"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Preparación de la depuración: Aplicaciones de Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La plantilla de proyecto de Windows Forms crea una aplicación de Windows Forms. La depuración de este tipo de aplicación en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es muy sencilla. Para obtener más información, consulte [Creación de un proyecto de aplicación de Windows](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Cuando se crea un proyecto de formularios Windows Forms con la plantilla de proyecto, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea automáticamente la configuración requerida para las versiones Debug y Release. Si fuera necesario, puede cambiar esta configuración. Esta configuración se puede cambiar en el cuadro de diálogo ** \<project name> páginas de propiedades** (**mi proyecto** en Visual Basic).  
  
 Para obtener más información, consulte [Valores de propiedades recomendados](../debugger/managed-debugging-recommended-property-settings.md).  
  
 En la tabla siguiente se muestra una configuración de propiedades adicional recomendada.  
  
### <a name="configuration-properties-in-debug-tab"></a>Propiedades de configuración de la ficha Depurar  
  
|**Nombre de la propiedad**|**Configuración**|  
|-----------------------|-----------------|  
|**Acción de inicio**|- Establézcala en **Proyecto de inicio** en la mayoría de los casos. Establézcala en **Programa externo de inicio** para iniciar otro ejecutable al comenzar la depuración (normalmente para la depuración de archivos DLL).|  
  
 Es posible depurar aplicaciones de Windows Forms dentro de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o mediante la asociación a una aplicación que ya está en ejecución. Para obtener más información sobre cómo crear asociaciones, consulte [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Para depurar una aplicación de Windows Forms en C#, F# o Visual Basic  
  
1. Abra el proyecto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Cree puntos de interrupción según sea necesario.  
  
    Debido a que las aplicaciones de Windows Forms están orientadas a eventos, los puntos de interrupción entrarán en el código del controlador de eventos o en métodos llamados por el código del controlador de eventos. Entre los eventos típicos en los cuales colocar puntos de interrupción se encuentran:  
  
   1. Eventos asociados a un control, como Click, Enter, etc.  
  
   2. Eventos asociados al inicio y apagado de una aplicación como Load, Activated, etc.  
  
   3. Eventos de foco y validación.  
  
      Para más información, consulte el artículo sobre [creación de controladores de eventos en Windows Forms](https://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. En el menú **Depurar**, haga clic en **Iniciar**.  
  
4. Depure con las técnicas descritas en [conceptos básicos del depurador](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Consulte también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyectos de C#, F # y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Cómo: establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Configuración del proyecto para las configuraciones de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración del proyecto para una configuración de depuración Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](https://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)
