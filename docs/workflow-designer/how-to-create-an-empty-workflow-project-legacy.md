---
title: "Cómo: crear un proyecto de flujo de trabajo vacío (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- projects, empty workflow
- empty workflow projects
- workflows, empty workflow projects
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 70c7427efa093d7af42b18e694fbf068d52624f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-empty-workflow-project-legacy"></a>Cómo: Crear un proyecto de flujo de trabajo vacío (Heredado)
Siga estos pasos para crear un proyecto de flujo de trabajo vacío mediante [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado proporcionado por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-an-empty-workflow-project"></a>Para crear un proyecto de flujo de trabajo vacío  
  
1.  Inicie Visual Studio.  
  
2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3.  Seleccione el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    >  La opción predeterminada de [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que tienen como destino [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] y no usa el diseñador heredado.  
  
4.  En el **tipos de proyecto** panel, seleccione Visual C# o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.  
  
5.  En el **plantillas** panel, seleccione **proyecto vacío de flujo de trabajo**.  
  
6.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.  
  
     Si desea que un directorio de solución creado para el proyecto, seleccione la **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.  
  
8.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)