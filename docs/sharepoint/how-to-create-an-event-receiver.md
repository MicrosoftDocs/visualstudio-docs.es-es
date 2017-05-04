---
title: "C&#243;mo: Crear un receptor de eventos | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "receptores de eventos [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, receptores de eventos"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Crear un receptor de eventos
  Crear *los receptores de eventos*, puede responder cuando un usuario interactúa con los elementos de SharePoint como listas o elementos de lista.  Por ejemplo, el código de un receptor de eventos puede ser se desencadena cuando un usuario cambia el calendario o elimina un nombre de una lista de contactos.  Siguiendo este tema, puede obtener información sobre cómo agregar un receptor de eventos a una instancia de lista.  
  
 Para completar estos pasos, debe tener instalado [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y las ediciones compatibles de Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Dado que este ejemplo requiere un proyecto de SharePoint, también debe haber completado el procedimiento del tema [Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## Agregar un controlador de eventos  
 El proyecto que creó en [Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) incluye columnas de sitio personalizadas, una lista personalizada, y un tipo de contenido.  En el siguiente procedimiento, se expandirá este proyecto agregando un controlador de eventos simple \(receptor de eventos\) a una instancia de lista para mostrar cómo controlar los eventos que se producen en los elementos de SharePoint como listas.  
  
#### Para agregar un receptor de eventos a la instancia de la lista  
  
1.  Abra el proyecto que creó en [Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  En **Explorador de soluciones**, elija el nodo de proyecto de SharePoint, que se denomina **Sesión**.  
  
3.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
4.  En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el elemento de **2010** .  
  
5.  En el panel de **Plantillas** , elija **receptor de eventos**, denomínelo TestEventReceiver1, y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
6.  En la lista de **Qué tipo de receptor de eventos desea usar?** , elija **Eventos de elementos de lista**.  
  
7.  En la lista de **Qué elemento debe ser el origen del evento?** , elija **Pacientes \(Clinic\\Patients\)**.  
  
8.  En la lista de **Controlar los siguientes eventos** , active la casilla situada junto a **Se agregó un elemento**, y después elija el botón de **Finalizar** .  
  
     El archivo de código del receptor de nuevo evento contiene un método denominado `ItemAdded`.  En el paso siguiente, agregará código a este método para que cada contacto se llamará Scott brown de forma predeterminada.  
  
9. Reemplace el método existente de `ItemAdded` con el código siguiente, y elija la tecla F5:  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Se ejecuta el código, y el sitio de SharePoint aparece en el explorador web.  
  
10. En la barra de inicio rápido, elija el vínculo de **Pacientes** , y elija el vínculo de **Agregar nuevo elemento** .  
  
     El formulario de entrada para los nuevos elementos se abre.  
  
11. Escriba los datos en los campos, y elija el botón de **Guardar** .  
  
     Después de elegir el botón de **Guardar** , las actualizaciones de la columna de **Nombre paciente** automáticamente el nombre Scott broncean.  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  