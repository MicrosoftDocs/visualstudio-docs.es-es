---
title: 'Cómo: crear una biblioteca de actividades | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662753"
---
# <a name="how-to-create-an-activity-library"></a>Crear una biblioteca de actividades
Las actividades personalizadas se usan para modelar los procesos de negocio concretos de un flujo de trabajo. La plantilla Biblioteca de actividad de [!INCLUDE[vs2010](../includes/vs2010-md.md)] se ha proporcionado para que pueda crear tales actividades personalizadas visualmente mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)].

### <a name="to-create-a-workflow-activity-library"></a>Para crear una biblioteca de actividades de flujo de trabajo

1. Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. En el menú **archivo** , seleccione **nuevo**y, a continuación, seleccione **proyecto..**..

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3. En el panel **tipos de proyecto** , seleccione flujo de **trabajo** de los proyectos de **Visual C#** o agrupaciones de **Visual Basic** en función de su preferencia de idioma.

4. En el panel **plantillas** , seleccione **biblioteca de actividades**.

5. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

6. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.

7. En el cuadro **solución** , escriba un nombre descriptivo para la solución y, a continuación, haga clic en **Aceptar**.

    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)] , haga clic con el botón derecho en la solución en **Explorador de soluciones**y seleccione **Agregar**y luego **nuevo proyecto...** para abrir el cuadro de diálogo **nuevo proyecto** . Continúe de la forma descrita anteriormente en este procedimiento.

8. La plantilla de proyecto crea una definición de actividad en XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] se abre y muestra el lienzo para su actividad personalizada.

9. Arrastre una actividad del **cuadro de herramientas** a la superficie de diseño para incluirla en la actividad personalizada.

    > [!CAUTION]
    > Solo puede tener una actividad secundaria en el cuerpo de la actividad personalizada; sin embargo, esa actividad de elemento secundario podría ser una actividad compuesta, como una actividad <xref:System.Activities.Statements.Sequence> o una actividad <xref:System.Activities.Statements.Flowchart>.

## <a name="see-also"></a>Consulte también
 [Cómo: crear una actividad](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)