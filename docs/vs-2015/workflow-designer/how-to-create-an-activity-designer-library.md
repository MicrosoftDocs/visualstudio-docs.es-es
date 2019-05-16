---
title: Procedimiento Crear una biblioteca de diseñadores de actividad | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a51b4cdb67590b908bc406b78c04ddf0c5aa3e2f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694558"
---
# <a name="how-to-create-an-activity-designer-library"></a>Procedimiento Crear una biblioteca de diseñadores de actividades
Los diseñadores de actividades personalizados permiten crear una interfaz de usuario para una actividad estándar o personalizada. El usuario controla la complejidad de la interfaz de usuario y tiene la capacidad de crear más de un diseñador de actividad para una actividad. Este escenario permite crear diseñadores que se adaptan a múltiples audiencias.  
  
### <a name="to-create-an-activity-designer-library"></a>Para crear una biblioteca de diseñadores de actividades  
  
1. Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto...** Para abrir el **nuevo proyecto** cuadro de diálogo.  
  
3. En el **tipos de proyecto** panel, seleccione **flujo de trabajo** desde el **Visual C#** o **Visual Basic** agrupaciones según su preferido lenguaje.  
  
4. En el **plantillas** panel, seleccione **biblioteca del Diseñador de actividad**.  
  
5. En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
6. En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.  
  
7. En el **solución** cuadro, escriba un nombre descriptivo para la solución y luego haga clic en **Aceptar**.  
  
    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujo de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)], haga clic con el botón derecho en la solución en **el Explorador de soluciones**y seleccione **agregar**, a continuación, **Nuevo proyecto...** Para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.  
  
8. La plantilla de proyecto crea una definición del diseñador de actividad en código XAML y el archivo de implementación subyacente está en código fuente. [!INCLUDE[wfd1](../includes/wfd1-md.md)] se abre y muestra el lienzo para su diseñador de actividades.  
  
9. Arrastre [!INCLUDE[avalon1](../includes/avalon1-md.md)] controla desde el **cuadro de herramientas** hasta la superficie de diseño para usarlos en el Diseñador de actividad personalizado.  Para obtener un ejemplo de cómo implementar un diseñador de actividad personalizado, vea [Cómo: Crear un diseñador de actividad personalizado](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).  
  
    > [!WARNING]
    > Diseñadores de actividad personalizados se pueden usar para actividades personalizadas, así como para predeterminada [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]actividades.  
  
## <a name="see-also"></a>Vea también  
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)