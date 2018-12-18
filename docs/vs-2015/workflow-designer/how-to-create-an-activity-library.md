---
title: 'Cómo: crear una biblioteca de actividades | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 341e87459cbaae204baba66108a5944eb1f7f97f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271837"
---
# <a name="how-to-create-an-activity-library"></a>Crear una biblioteca de actividades
Las actividades personalizadas se usan para modelar los procesos de negocio concretos de un flujo de trabajo. La plantilla Biblioteca de actividad de [!INCLUDE[vs2010](../includes/vs2010-md.md)] se ha proporcionado para que pueda crear tales actividades personalizadas visualmente mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
### <a name="to-create-a-workflow-activity-library"></a>Para crear una biblioteca de actividades de flujo de trabajo  
  
1.  Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto...** .  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3.  En el **tipos de proyecto** panel, seleccione **flujo de trabajo** desde el **Visual C#** proyectos o **Visual Basic** agrupaciones en función de su preferencia de idioma.  
  
4.  En el **plantillas** panel, seleccione **biblioteca de actividades**.  
  
5.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
6.  En el **ubicación** cuadro, escriba en el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.  
  
7.  En el **solución** cuadro, escriba un nombre descriptivo para la solución y luego haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Si desea agregar una aplicación de consola de flujo de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)], haga clic en la solución de **el Explorador de soluciones**y seleccione **agregar**, a continuación,  **Nuevo proyecto...** Para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.  
  
8.  La plantilla de proyecto crea una definición de actividad en XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] se abre y muestra el lienzo para su actividad personalizada.  
  
9. Arrastre una actividad desde la **cuadro de herramientas** hasta la superficie de diseño para incluirla en su actividad personalizada.  
  
    > [!CAUTION]
    >  Solo puede tener una actividad secundaria en el cuerpo de la actividad personalizada; sin embargo, esa actividad de elemento secundario podría ser una actividad compuesta, como una actividad <xref:System.Activities.Statements.Sequence> o una actividad <xref:System.Activities.Statements.Flowchart>.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear una actividad](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)