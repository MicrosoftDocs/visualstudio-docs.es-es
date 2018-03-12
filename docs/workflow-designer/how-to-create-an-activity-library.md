---
title: "Cómo: crear una biblioteca de actividades | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 151e3f84636273de253937ebf5c91cff066b9f85
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-an-activity-library"></a>Crear una biblioteca de actividades
Las actividades personalizadas se usan para modelar los procesos de negocio concretos de un flujo de trabajo. La plantilla Biblioteca de actividades en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] se ha proporcionado para que pueda crear tales actividades personalizadas visualmente mediante el Diseñador de flujo de trabajo de Windows.

### <a name="to-create-a-workflow-activity-library"></a>Para crear una biblioteca de actividades de flujo de trabajo

1.  Inicie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto...** .

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3.  En el **tipos de proyecto** panel, seleccione **flujo de trabajo** desde el **Visual C#** proyectos o **Visual Basic** agrupaciones en función de su preferencia de idioma.

4.  En el **plantillas** panel, seleccione **biblioteca de actividades**.

5.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

6.  En el **ubicación** cuadro, escriba en el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.

7.  En el **solución** cuadro, escriba un nombre descriptivo para la solución y haga clic en **Aceptar**.

    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], haga clic en la solución de **el Explorador de soluciones**y seleccione **agregar**, a continuación,  **Nuevo proyecto...**  para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.

8.  La plantilla de proyecto crea una definición de actividad en XAML. Diseñador de flujo de trabajo de Windows abre y muestra el lienzo para su actividad personalizada.

9. Arrastre una actividad desde la **cuadro de herramientas** hasta la superficie de diseño para incluirla en la actividad personalizada.

    > [!CAUTION]
    > Solo puede tener una actividad secundaria en el cuerpo de la actividad personalizada; sin embargo, esa actividad de elemento secundario podría ser una actividad compuesta, como una actividad <xref:System.Activities.Statements.Sequence> o una actividad <xref:System.Activities.Statements.Flowchart>.

## <a name="see-also"></a>Vea también

- [Cómo crear una actividad](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)