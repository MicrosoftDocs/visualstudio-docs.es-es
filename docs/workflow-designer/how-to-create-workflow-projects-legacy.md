---
title: "Cómo: crear proyectos de flujo de trabajo (heredado) | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dc38c6b323ee06ed9b312811eb892e7654134d05
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Cómo: Crear proyectos de flujo de trabajo (Heredado)
Siga estos pasos para crear un proyecto de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que tenga como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]. Este procedimiento utiliza el Diseñador de flujo de trabajo de Windows heredado proporcionado por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

### <a name="to-create-a-workflow-project"></a>Para crear un proyecto de flujo de trabajo

1.  Inicie [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].

2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3.  Seleccione el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada de [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que tienen como destino [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] y no usa el diseñador heredado.

4.  En el **tipos de proyecto** panel, seleccione proyectos de Visual C# o proyectos de Visual Basic y, a continuación, seleccione **flujo de trabajo**.

5.  En el **plantillas** panel, seleccione una de las plantillas de proyecto instaladas:

    -   Aplicación de consola de flujos de trabajo secuenciales

    -   Biblioteca de flujos de trabajo secuenciales

    -   Biblioteca de flujos de trabajo de actividad

    -   Aplicación de consola de flujos de trabajo de equipo de estado

    -   Biblioteca de flujos de trabajo de equipo de estado

    -   Proyecto de flujo de trabajo vacío

6.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta el directorio.

     Si desea que un directorio de solución creado para el proyecto, seleccione la **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.

8.  Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)