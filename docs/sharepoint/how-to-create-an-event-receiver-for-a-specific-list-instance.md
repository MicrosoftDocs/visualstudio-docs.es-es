---
title: "C&#243;mo: Crear un receptor de eventos para una instancia de lista gen&#233;rica | Microsoft Docs"
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
  - "receptores de eventos [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, receptores de eventos"
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Crear un receptor de eventos para una instancia de lista gen&#233;rica
  Un receptor de eventos de instancia de lista responde a los eventos que se producen en cualquier instancia de una definición de lista.  Aunque la plantilla de receptor de eventos no habilita el destino de una instancia de lista concreta, se puede modificar un receptor de eventos cuyo ámbito es una definición de lista para responder a los eventos en una instancia de lista concreta.  
  
 Para destinarla a una instancia de lista concreta, en el archivo Elements.xml correspondiente al receptor de eventos, reemplace `ListTemplateId` con `ListUrl` y agregue la dirección URL de la instancia de lista.  
  
## Crear un receptor de eventos de una instancia de lista  
 Los siguientes pasos muestran cómo modificar un receptor de eventos del elemento de lista para responder únicamente a los eventos que se producen en una instancia de lista de anuncios personalizada.  
  
#### Para modificar un receptor de eventos para responder a una instancia de lista concreta  
  
1.  En un explorador, abra el sitio de SharePoint.  
  
2.  En el panel de navegación, vínculo de **Listas** .  
  
3.  En la página de **Todo el contenido del sitio** , elija el vínculo de **crear** .  
  
4.  En el cuadro de diálogo de **crear** , elija el tipo de **Anuncios** , llame al anuncio TestAnnouncements, y elija el botón de **crear** .  
  
5.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de receptor de eventos.  
  
6.  En la lista de **Qué tipo de receptor de eventos desea usar?** , elija **Eventos de elementos de lista**.  
  
    > [!NOTE]  
    >  También puede seleccionar cualquier otro tipo de receptor de eventos cuyo ámbito sea una definición de lista, por ejemplo, **Eventos de correo electrónico de la lista** o **Eventos de flujo de trabajo de lista**.  
  
7.  En la lista de **Qué elemento debe ser el origen del evento?** , elija **Anuncios**.  
  
8.  En la lista de **Controlar los siguientes eventos** , active la casilla de **Se va a agregar un elemento** , y después elija el botón de **Finalizar** .  
  
9. En **Explorador de soluciones**, bajo EventReceiver1, abra Elements.xml.  
  
     El receptor de eventos hace referencia actualmente la definición de lista de anuncios mediante la siguiente línea:  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Cambie esta línea al texto siguiente:  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Así se dirige el receptor de eventos para responder solo a los eventos que se producen en la nueva lista de anuncios **TestAnnouncements** que acaba de crear.  Puede cambiar el atributo `ListURL` para hacer referencia a cualquier instancia de lista en el servidor de SharePoint.  
  
10. Abra el archivo de código del receptor de eventos y coloque un punto de interrupción en el método ItemAdding.  
  
11. Elija la tecla F5 para compilar y ejecutar la solución.  
  
12. En SharePoint, elija el vínculo de **TestAnnouncements** en el panel de navegación.  
  
13. Elija el vínculo de **Agregue el nuevo anuncio** .  
  
14. Escriba un título para el anuncio, y elija el botón de **Guardar** .  
  
     Observe que se llega al punto de interrupción cuando el nuevo elemento se agrega a la lista de anuncios personalizada.  
  
15. Elija la tecla F5 para reanudar.  
  
16. En el panel de navegación, elija el vínculo de **Listas** , y elija el vínculo de **Anuncios** .  
  
17. Agregue un nuevo anuncio.  
  
     Observe que el receptor de eventos no se activa en el nuevo anuncio porque el receptor está configurado para responder sólo a los eventos de la instancia de lista de anuncios personalizada, **TestAnnouncements**.  
  
## Vea también  
 [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  