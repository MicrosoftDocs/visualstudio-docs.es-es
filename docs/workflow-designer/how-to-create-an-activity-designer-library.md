---
title: "Cómo: crear una biblioteca del Diseñador de actividad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84f483c4e280dbf5c1dc303805028456cd1ff59e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-an-activity-designer-library"></a>Crear una biblioteca de diseñadores de actividades
Los diseñadores de actividades personalizados permiten crear una interfaz de usuario para una actividad estándar o personalizada. El usuario controla la complejidad de la interfaz de usuario y tiene la capacidad de crear más de un diseñador de actividad para una actividad. Este escenario permite crear diseñadores que se adaptan a múltiples audiencias.  
  
### <a name="to-create-an-activity-designer-library"></a>Para crear una biblioteca de diseñadores de actividades  
  
1.  Inicie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto...**  para abrir el **nuevo proyecto** cuadro de diálogo.  
  
3.  En el **tipos de proyecto** panel, seleccione **flujo de trabajo** desde el **Visual C#** o **Visual Basic** agrupaciones según su preferido idioma.  
  
4.  En el **plantillas** panel, seleccione **biblioteca del Diseñador de actividad**.  
  
5.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
6.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.  
  
7.  En el **solución** cuadro, escriba un nombre descriptivo para la solución y haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], haga clic con el botón secundario en la solución en **el Explorador de soluciones**y seleccione **agregar**, a continuación, **Nuevo proyecto...**  para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.  
  
8.  La plantilla de proyecto crea una definición del diseñador de actividad en código XAML y el archivo de implementación subyacente está en código fuente. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] se abre y muestra el lienzo para su diseñador de actividades.  
  
9. Arrastre [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] controla desde el **cuadro de herramientas** hasta la superficie de diseño para utilizarlos en el Diseñador de actividad personalizados.  Para obtener un ejemplo de cómo implementar un diseñador de actividad personalizado, consulte [Cómo: crear un diseñador de actividad personalizado](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).  
  
    > [!WARNING]
    >  Diseñadores de actividad personalizados pueden usarse para actividades personalizadas, así como para predeterminado [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]actividades.  
  
## <a name="see-also"></a>Vea también  
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)