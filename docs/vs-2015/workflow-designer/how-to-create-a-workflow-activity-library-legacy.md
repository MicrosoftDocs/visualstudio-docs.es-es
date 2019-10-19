---
title: 'Cómo: crear una biblioteca de actividades de flujo de trabajo (heredado) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604959"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Cómo: Crear una biblioteca de actividades de flujo de trabajo (Heredado)
Siga estos pasos para crear un proyecto de biblioteca de actividades de flujo de trabajo mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-workflow-activity-library-project"></a>Para crear un proyecto de biblioteca de actividades de flujo de trabajo

1. Inicie Visual Studio.

2. En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3. Seleccione la opción **.NET Framework 3,0** o la opción **.NET Framework 3,5** en la lista desplegable de la parte superior de la ventana **nuevo proyecto** para obtener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada en [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.

4. En el **Panel tipos de proyecto** , seleccione C# visual o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.

5. En el panel **plantillas** , seleccione **biblioteca de actividades de flujo de trabajo**.

6. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

7. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.

     Si desea crear un directorio de soluciones para el proyecto, active la casilla **Crear directorio para la solución** y escriba un nombre en el cuadro Nombre de la **solución** .

8. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md) [mediante el diseñador de actividad](../workflow-designer/using-the-legacy-activity-designer.md) heredado [actividades de flujo](../workflow-designer/legacy-workflow-activities.md) de trabajo [desarrollar actividades de flujo](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52) de trabajo [Windows Workflow Foundation actividades](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)