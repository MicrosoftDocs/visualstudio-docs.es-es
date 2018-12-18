---
title: 'Cómo: crear controladores de eventos en proyectos de Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8b7e55ee7f094ad104d9c8eb6ef3057621bcccee
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254249"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Cómo: crear controladores de eventos en proyectos de Office
  Hay varias maneras de crear controladores de eventos en Visual Basic y C#. En la vista Diseño, puede crear el valor predeterminado los controladores de eventos para controles haciendo doble clic en el control, o utilice el panel de eventos de la **propiedades** ventana para crear controladores para cualquier evento en el control. Sin embargo, si está en la vista código, es posible que no desea cambiar a vista de diseño para crear un controlador de eventos.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Para crear un controlador de eventos en Visual Basic  
  
1.  Desde el **nombre de la clase** lista desplegable en la parte superior del Editor de código, seleccione el objeto que desea crear un controlador de eventos.  
  
    > [!NOTE]  
    >  Si desea crear controladores de eventos para `ThisDocument` o `ThisWorkbook`, debe seleccionar **(eventos ThisDocument)** o **(eventos ThisWorkbook)** en el **nombre de la clase**lista desplegable  
  
2.  Desde el **nombre del método** lista desplegable en la parte superior del Editor de código, seleccione el evento.  
  
     Visual Studio crea el controlador de eventos y el punto de inserción desplaza al controlador de eventos recién creado. Si ya existe el controlador de eventos, el punto de inserción se desplaza al controlador de eventos existente.  
  
### <a name="to-create-an-event-handler-in-c"></a>Para crear un controlador de eventos en C#  
  
1.  Crear el delegado de eventos en el **inicio** eventos de la clase escribiendo el nombre del evento calificado seguido por un espacio y, a continuación, escriba **+=** posteriormente sin espacio. Por ejemplo:  
  
     `this.<object name>.<event name> +=`  
  
2.  Al final de la línea de código, presione la tecla TAB dos veces.  
  
     Visual Studio automáticamente completa la línea de código, crea el controlador de eventos y el punto de inserción desplaza al controlador de eventos recién creado.  
  
## <a name="see-also"></a>Vea también  
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Tutorial: Programar basándose en eventos de un control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)  
  
  