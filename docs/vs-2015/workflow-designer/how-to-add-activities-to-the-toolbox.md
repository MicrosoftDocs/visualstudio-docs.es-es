---
title: 'Cómo: agregar actividades al cuadro de herramientas | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 66595a4aac8ae32c10223b30e6901decc630b10f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574241"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Cómo agregar actividades al cuadro de herramientas
Se pueden agregar actividades a la **cuadro de herramientas** en la solución de varias maneras diferentes. Puede agregarlas desde dentro de su proyecto actual y hacer referencia a las misas desde un proyecto diferente o desde un ensamblado diferente.  
  
### <a name="to-add-an-activity-from-within-your-current-project"></a>Para agregar una actividad desde su proyecto actual  
  
1.  Agregue una nueva actividad personalizada al proyecto de flujo de trabajo actual. [!INCLUDE[crabout](../includes/crabout-md.md)] Agregar una nueva actividad personalizada al proyecto, vea [Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).  
  
2.  Agregue lógica personalizada a su actividad.  
  
3.  Compile el proyecto. Si la compilación se realizó correctamente, una nueva categoría en la **cuadro de herramientas** denominado "\<*nombre del proyecto*>" se muestra con la actividad personalizada incluida en esa categoría.  
  
    > [!NOTE]
    >  Si se restablece el cuadro de herramientas, las actividades personalizadas se quitarán, incluso si la solución se compila de nuevo. Para volver a rellenar el cuadro de herramientas con actividades personalizadas después de que se haya restablecido, reinicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  El cuadro de herramientas solo puede mostrar una actividad de un nombre especificado. Si dos actividades de distintos ensamblados tienen el mismo nombre de clase, solo se mostrará una.  
  
    > [!NOTE]
    >  El dominio de aplicación se comparte entre las instancias del editor; si se usan variables estáticas, se compartirán entre las instancias del editor también. Si este no es el comportamiento deseado, se debe usar un servicio para hacer un seguimiento de las instancias variables. Consulte [utilizando el contexto de edición de ModelItem](http://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1) para obtener información sobre el uso de servicios dentro del diseñador.  
  
### <a name="to-add-an-activity-from-within-a-different-project"></a>Para agregar una actividad desde un proyecto diferente  
  
1.  Abra una solución que contenga al menos un proyecto de flujo de trabajo y un proyecto de biblioteca de actividades personalizado u otro proyecto de flujo de trabajo que defina una actividad personalizada.  
  
2.  Compile ambos proyectos. Si las compilaciones se efectúan correctamente, una nueva categoría en la **cuadro de herramientas** denominado "\<*nombre del proyecto*>" se muestra con la actividad personalizada incluida en esa categoría.  
  
### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Para agregar una actividad al cuadro de herramientas desde un ensamblado  
  
1.  Abra una solución de flujo de trabajo.  
  
2.  Desde el **herramientas** menú, seleccione **elegir elementos del cuadro de herramientas...** .  
  
3.  En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, seleccione el **componentes de System.Activities** pestaña, a continuación, haga clic en **Examinar...** para navegar hasta el ensamblado que contiene la actividad personalizada que se va a agregar.  
  
4.  Seleccione el ensamblado y haga clic en **Aceptar**. El componente de actividad personalizado se agrega a la lista de componentes y se selecciona automáticamente.  
  
    1.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.  
  
5.  Para mostrar el cuadro de herramientas, seleccione **cuadro de herramientas** desde el **vista** menú.  
  
6.  La actividad personalizada aparece en la **cuadro de herramientas** en la categoría que fue el foco antes de que se agregó el elemento. Por ejemplo, si la **General** categoría se ha seleccionado en el **cuadro de herramientas** antes de agregar el elemento de cuadro de herramientas, la actividad aparezca bajo el **General** categoría.  
  
## <a name="see-also"></a>Vea también  
 [Usar el Diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md)