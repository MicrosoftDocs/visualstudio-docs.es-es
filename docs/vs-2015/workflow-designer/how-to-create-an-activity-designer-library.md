---
title: 'Cómo: crear una biblioteca del diseñador de actividad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662868"
---
# <a name="how-to-create-an-activity-designer-library"></a>Crear una biblioteca de diseñadores de actividades
Los diseñadores de actividades personalizados permiten crear una interfaz de usuario para una actividad estándar o personalizada. El usuario controla la complejidad de la interfaz de usuario y tiene la capacidad de crear más de un diseñador de actividad para una actividad. Este escenario permite crear diseñadores que se adaptan a múltiples audiencias.

### <a name="to-create-an-activity-designer-library"></a>Para crear una biblioteca de diseñadores de actividades

1. Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. En el menú **archivo** , seleccione **nuevo**y, a continuación, seleccione **proyecto...** para abrir el cuadro de diálogo **nuevo proyecto** .

3. En el panel **tipos de proyecto** , seleccione flujo de **trabajo** desde las agrupaciones de **Visual C#** o **Visual Basic** en función del idioma que prefiera.

4. En el panel **plantillas** , seleccione **biblioteca del diseñador de actividad**.

5. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

6. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.

7. En el cuadro **solución** , escriba un nombre descriptivo para la solución y, a continuación, haga clic en **Aceptar**.

    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)] , haga clic con el botón derecho en la solución en **Explorador de soluciones**y seleccione **Agregar**y luego **nuevo proyecto...** para abrir el cuadro de diálogo **nuevo proyecto** . Continúe de la forma descrita anteriormente en este procedimiento.

8. La plantilla de proyecto crea una definición del diseñador de actividad en código XAML y el archivo de implementación subyacente está en código fuente. [!INCLUDE[wfd1](../includes/wfd1-md.md)] se abre y muestra el lienzo para su diseñador de actividades.

9. Arrastre los [!INCLUDE[avalon1](../includes/avalon1-md.md)] controles del **cuadro de herramientas** a la superficie de diseño para usarlos en el diseñador de actividad personalizado.  Para obtener un ejemplo de cómo implementar un diseñador de actividad personalizado, vea [Cómo: crear un diseñador de actividad personalizado](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Los diseñadores de actividad personalizados se pueden usar para las actividades personalizadas y para [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] las actividades predeterminadas.

## <a name="see-also"></a>Consulte también
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)