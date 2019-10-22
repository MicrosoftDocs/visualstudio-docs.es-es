---
title: 'Cómo: crear una biblioteca de flujos de trabajo de equipo de estado (heredado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3cff5d6aaa28915524b7699affdf41d3bebef4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663379"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Cómo: Crear un biblioteca de flujos de trabajo de equipo de estado (Heredado)
Siga estos pasos para crear un proyecto de biblioteca de flujos de trabajo de equipo de estado mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Para crear un proyecto de biblioteca de flujos de trabajo de equipo de estado

1. Inicie Visual Studio.

2. En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3. Seleccione la opción **.NET Framework 3,0** o la opción **.NET Framework 3,5** en la lista desplegable de la parte superior de la ventana **nuevo proyecto** para obtener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada en [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.

4. En el **Panel tipos de proyecto** , seleccione C# visual o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.

5. En el panel **plantillas** , seleccione **biblioteca de flujos de trabajo de equipo de estado**.

6. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

7. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.

     Si desea crear un directorio de soluciones para el proyecto, active la casilla **Crear directorio para la solución** y escriba un nombre en el cuadro Nombre de la **solución** .

8. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
 Creación de flujos de trabajo de [equipo de estado](https://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d) proyectos de [flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)