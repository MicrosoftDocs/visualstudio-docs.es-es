---
title: Procedimiento Crear una biblioteca de actividades de flujo de trabajo (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9baa358c3728c6cbedc5f8768b29ba7efe64b399
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703289"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Procedimiento Crear una biblioteca de actividades de flujo de trabajo (heredado)
Siga estos pasos para crear un proyecto de biblioteca de actividades de flujo de trabajo mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-workflow-activity-library-project"></a>Para crear un proyecto de biblioteca de actividades de flujo de trabajo  
  
1. Inicie Visual Studio.  
  
2. En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3. Seleccione el **.NET Framework 3.0** opción o el **.NET Framework 3.5** opción en la lista desplegable situada en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    > La opción predeterminada de [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.  
  
4. En el **tipos de proyecto** panel, seleccione Visual C# o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.  
  
5. En el **plantillas** panel, seleccione **Workflow Activity Library**.  
  
6. En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
7. En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.  
  
     Si desea que un directorio de soluciones creado para el proyecto, seleccione el **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.  
  
8. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Usar el Diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Actividades de flujo de trabajo heredado](../workflow-designer/legacy-workflow-activities.md)   
 [Desarrollar actividades de flujo de trabajo](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52)   
 [Actividades de Windows Workflow Foundation](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)