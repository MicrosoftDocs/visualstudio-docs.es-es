---
title: "C&#243;mo: Crear controladores de eventos en proyectos de Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controladores de eventos [desarrollo de Office en Visual Studio]"
  - "eventos [desarrollo de Office en Visual Studio]"
  - "Visual Basic [desarrollo de Office en Visual Studio], controladores de eventos"
  - "Visual C# [desarrollo de Office en Visual Studio], controladores de eventos"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# C&#243;mo: Crear controladores de eventos en proyectos de Office
  Existen varias maneras de crear controladores de eventos en Visual Basic y en C\#.  En la vista Diseño, puede crear el controlador de eventos predeterminado para controles haciendo doble clic en el control, o usar el panel de eventos de la ventana **Propiedades** para crear controladores para cualquier evento del control.  Sin embargo, si está en la vista Código, quizás no desee cambiar a la vista Diseño para crear un controlador de eventos.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Para crear un controlador de eventos en Visual Basic  
  
1.  En la lista desplegable **Nombre de clase** de la parte superior del Editor de código, elija el objeto para el que desea crear un controlador de eventos.  
  
    > [!NOTE]  
    >  Si desea crear controladores de eventos para `ThisDocument` o `ThisWorkbook`, debe seleccionar **\(Eventos ThisDocument\)** o **\(Eventos ThisWorkbook\)** en la lista desplegable **Nombre de clase**.  
  
2.  En la lista desplegable **Nombre de método** de la parte superior del Editor de código, seleccione el evento.  
  
     Visual Studio crea el controlador de eventos y lleva el punto de inserción al controlador de eventos recién creado.  Si ya existe el controlador de eventos, el punto de inserción se desplaza al controlador de eventos existente.  
  
### Para crear un controlador de eventos en C\#  
  
1.  Cree el delegado de eventos en el evento **Startup** de la clase; para ello, escriba el nombre de evento calificado seguido de un espacio y de \+\=, sin ningún espacio después.  Por ejemplo:  
  
     `this.<object name>.<event name> +=`  
  
2.  Al final de la línea de código, presione dos veces la tecla TAB.  
  
     Visual Studio finaliza automáticamente la línea de código, crea el controlador de eventos y lleva el punto de inserción al controlador de eventos recién creado.  
  
## Vea también  
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Tutorial: Programar basándose en los eventos de un control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)  
  
  