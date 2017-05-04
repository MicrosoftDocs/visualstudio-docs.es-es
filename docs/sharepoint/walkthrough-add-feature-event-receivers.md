---
title: "Tutorial: Agregar receptores de eventos de caracter&#237;sticas | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, herramientas para paquetes avanzadas"
  - "desarrollo de SharePoint en Visual Studio, receptores de eventos"
  - "desarrollo de SharePoint en Visual Studio, receptores de eventos de características"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Tutorial: Agregar receptores de eventos de caracter&#237;sticas
  Los receptores de eventos de características son métodos que se ejecutan cuando se produce uno de los eventos relacionados con las características siguientes en SharePoint:  
  
-   Se instala una característica.  
  
-   Se activa una característica.  
  
-   Se desactiva una característica.  
  
-   Se quita una característica.  
  
 En este tutorial se muestra cómo agregar un receptor de eventos a una característica en un proyecto SharePoint.  También se muestran las siguientes tareas:  
  
-   Crear un proyecto vacío con un receptor de eventos de característica.  
  
-   Controlar el método **FeatureDeactivating**.  
  
-   Utilizar el modelo de objetos de proyecto de SharePoint para agregar un anuncio a la lista Anuncios.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Crear un proyecto de receptor de eventos de característica  
 Primero, cree un proyecto para el receptor de eventos de característica.  
  
#### Para crear un proyecto con un receptor de eventos de característica  
  
1.  En la barra de menú, elija **archivo**, **new**, **Project** para mostrar el cuadro de diálogo de **Nuevo proyecto** .  
  
2.  Expanda el nodo de **sharepoint** en **Visual C\#** o **Visual Basic**y, a continuación el nodo de **2010** .  
  
3.  En el panel de **Plantillas** , elija la plantilla de **SharePoint 2010 Project** .  
  
     Utilice este tipo de proyecto para los receptores de eventos de característica porque no tienen ninguna plantilla de proyecto.  
  
4.  En el cuadro de **Name** , entre en FeatureEvtTest, y elija el botón de **Aceptar** para mostrar **Asistente para la personalización de SharePoint**.  
  
5.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL para el sitio de servidor de SharePoint al que desea agregar el nuevo elemento de campo personalizado, o utilice la ubicación predeterminada \(http:\/\/\<*system name*\>\/\).  
  
6.  En la sección **¿Cuál es el nivel de confianza de esta solución de SharePoint?**, elija el botón de opción **Implementar como solución de granja de servidores**.  
  
     Para obtener más información sobre soluciones de granja y soluciones en espacio aislado, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Elija el botón de **Finalizar** , y después observe que una característica denominada Característica1 aparece bajo el nodo de **Características** .  
  
## Agregar un receptor de eventos a la característica  
 A continuación agregue un receptor de eventos a la característica y agregue el código que ejecuta cuando la característica está desactivada.  
  
#### Para agregar un receptor de eventos a la característica  
  
1.  Abrir el menú contextual para el nodo características y, a continuación **Agregue la característica** para crear una característica.  
  
2.  Bajo el nodo de **Características** , abra el menú contextual para **Característica1**y, a continuación **Agregue al receptor de eventos** para agregar un receptor de eventos a la característica.  
  
     Esto agrega un archivo de código bajo Característica1.  En este caso, se denomina Feature1.EventReceiver.cs o Feature1.EventReceiver.vb, dependiendo del lenguaje de desarrollo de su proyecto.  
  
3.  Si el proyecto se escribe en [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], agregue el código siguiente al principio del receptor de eventos si aún no está ahí:  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  La clase del receptor de eventos contiene varios métodos comentados \- out que actúan como eventos.  Reemplace el método **FeatureDeactivating** por el siguiente método:  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## Probar el receptor de eventos de característica  
 A continuación, desactive la característica para comprobar si el método **FeatureDeactivating** genera un anuncio en la lista de anuncios de SharePoint.  
  
#### Para probar el receptor de eventos de característica  
  
1.  Establezca el valor de la propiedad de **Configuración de implementación activa** a **Sin activación**.  
  
     Estableciendo esta propiedad se evita que la característica se active en SharePoint y le permite depurar los receptores de eventos de características.  Para obtener más información, vea [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Elija la clave de **F5** para ejecutar el proyecto e implementarlo en SharePoint.  
  
3.  En la parte superior de la página Web de SharePoint, abra el menú de **Acciones del sitio** y, a continuación **Configuración del sitio**.  
  
4.  Bajo la sección de **Acciones del sitio** de la página de **Configuración del sitio** , elija el vínculo de **Administrar las características del sitio** .  
  
5.  En la página de **Características** , elija el botón de **Activación** junto a la característica de **FeatureEvtTest Característica1** .  
  
6.  En la página de **Características** , elija el botón de **Desactivar** junto a la característica de **FeatureEvtTest Característica1** , y elija el vínculo de confirmación de **Desactivar esta característica** para desactivar la característica.  
  
7.  Elija el botón de **Domicilio** .  
  
     Observe que aparece un anuncio en la lista **Anuncios** una vez desactivada la característica.  
  
## Vea también  
 [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  