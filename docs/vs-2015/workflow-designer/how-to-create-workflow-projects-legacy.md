---
title: 'Cómo: crear proyectos de flujo de trabajo (heredado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668675"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Cómo: Crear proyectos de flujo de trabajo (Heredado)
Siga estos pasos para crear un proyecto de [!INCLUDE[wf](../includes/wf-md.md)] que tenga como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. Este procedimiento usa [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)].

### <a name="to-create-a-workflow-project"></a>Para crear un proyecto de flujo de trabajo

1. Inicie [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

2. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3. Seleccione la opción **.NET Framework 3,0** o la opción **.NET Framework 3,5** en la lista desplegable de la parte superior de la ventana **nuevo proyecto** para obtener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada en [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.

4. En el panel **tipos de proyecto** , seleccione proyectos de Visual C# o proyectos de Visual Basic y, a continuación, seleccione flujo de **trabajo**.

5. En el panel **plantillas** , seleccione una de las plantillas de proyecto instaladas:

    - Aplicación de consola de flujos de trabajo secuenciales

    - Biblioteca de flujos de trabajo secuenciales

    - Biblioteca de flujos de trabajo de actividad

    - Aplicación de consola de flujos de trabajo de equipo de estado

    - Biblioteca de flujos de trabajo de equipo de estado

    - Proyecto de flujo de trabajo vacío

6. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

7. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para ir al directorio.

     Si desea crear un directorio de soluciones para el proyecto, active la casilla **Crear directorio para la solución** y escriba un nombre en el cuadro Nombre de la **solución** .

8. Haga clic en **OK**.

## <a name="see-also"></a>Consulte también
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)