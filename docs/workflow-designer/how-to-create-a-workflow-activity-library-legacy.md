---
title: "Cómo: crear una biblioteca de actividades de flujo de trabajo (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 20d017081ee1246d672ec052ce9924c35120c11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Cómo: Crear una biblioteca de actividades de flujo de trabajo (Heredado)
Siga estos pasos para crear un proyecto de biblioteca de actividades de flujo de trabajo mediante el uso de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado proporcionado por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-workflow-activity-library-project"></a>Para crear un proyecto de biblioteca de actividades de flujo de trabajo  
  
1.  Inicie Visual Studio.  
  
2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3.  Seleccione el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    >  La opción predeterminada de [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que tienen como destino [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] y no usa el diseñador heredado.  
  
4.  En el **tipos de proyecto** panel, seleccione Visual C# o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.  
  
5.  En el **plantillas** panel, seleccione **biblioteca de actividades de flujo de trabajo**.  
  
6.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.  
  
     Si desea que un directorio de solución creado para el proyecto, seleccione la **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.  
  
8.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de flujo de trabajo heredado](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Utilizar el Diseñador de actividades heredado](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Actividades de flujo de trabajo heredado](../workflow-designer/legacy-workflow-activities.md)   
 [Desarrollar actividades de flujo de trabajo](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)   
 [Actividades de Windows Workflow Foundation](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)