---
title: 'Cómo: crear controladores de eventos en proyectos de Office | Documentos de Microsoft'
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
ms.openlocfilehash: 833e41979d1dac9def7e647b396161d0ac5e2b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Cómo: Crear controladores de eventos en proyectos de Office
  Hay varias maneras de crear controladores de eventos en Visual Basic y C#. En la vista de diseño, puede crear controladores de eventos para controles del valor predeterminado haciendo doble clic en el control, o use el panel de eventos de la **propiedades** ventana Crear controladores para cualquier evento del control. Sin embargo, si está en la vista de código, no puede cambiar a la vista de diseño para crear un controlador de eventos.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Para crear un controlador de eventos en Visual Basic  
  
1.  Desde el **nombre de la clase** la lista desplegable en la parte superior del Editor de código, seleccione el objeto que desea crear un controlador de eventos.  
  
    > [!NOTE]  
    >  Si desea crear controladores de eventos para `ThisDocument` o `ThisWorkbook`, debe seleccionar **(eventos ThisDocument)** o **(eventos ThisWorkbook)** en el **nombre de la clase**lista desplegable  
  
2.  Desde el **nombre del método** lista desplegable en la parte superior del Editor de código, seleccione el evento.  
  
     Visual Studio crea el controlador de eventos y mueve el punto de inserción al controlador de eventos recién creado. Si ya existe el controlador de eventos, el punto de inserción se desplaza al controlador de eventos existente.  
  
### <a name="to-create-an-event-handler-in-c"></a>Para crear un controlador de eventos en C#  
  
1.  Crear el delegado de eventos en el **inicio** eventos de la clase escribiendo el nombre de evento completo seguido por un espacio y, a continuación, escriba **+=** sin ningún espacio después. Por ejemplo:  
  
     `this.<object name>.<event name> +=`  
  
2.  Al final de la línea de código, presione la tecla TAB dos veces.  
  
     Visual Studio automáticamente completa de la línea de código, crea el controlador de eventos y mueve el punto de inserción al controlador de eventos recién creado.  
  
## <a name="see-also"></a>Vea también  
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Tutorial: Programar basándose en eventos de un Control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Compilación de soluciones de Office](../vsto/building-office-solutions.md)  
  
  