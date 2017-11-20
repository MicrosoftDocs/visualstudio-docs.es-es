---
title: "Cómo: crear aplicaciones de consola de flujos de trabajo secuenciales (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e9732334f422b4042f2cd581afaea06bf99ab16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Cómo: Crear aplicaciones de consola de flujos de trabajo secuenciales (Heredado)
Siga estos pasos para crear un proyecto de aplicación de consola de flujos de trabajo secuenciales mediante el uso de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado proporcionado por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Para crear una aplicación de consola de flujos de trabajo secuenciales  
  
1.  Inicie Visual Studio.  
  
2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3.  Seleccione el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    >  La opción predeterminada de [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que tienen como destino [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] y no usa el diseñador heredado.  
  
4.  En el **tipos de proyecto** panel, seleccione proyectos de Visual C# o proyectos de Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.  
  
5.  En el **plantillas** panel, seleccione **aplicación de consola de flujos de trabajo secuenciales**.  
  
6.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.  
  
     Se abrirá el Diseñador de Windows Forms, que mostrará el formulario Form1 del proyecto creado.  
  
8.  Haga clic en **Aceptar**.  
  
     Se abre el Diseñador de flujo de trabajo y muestra la superficie de diseño de flujo de trabajo del flujo de trabajo secuencial que ha creado.  
  
9. Arrastre una actividad desde la **cuadro de herramientas** a la superficie de diseño en el **coloque la actividad** área designada.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de flujo de trabajo heredado](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Desarrollo de flujos de trabajo](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)