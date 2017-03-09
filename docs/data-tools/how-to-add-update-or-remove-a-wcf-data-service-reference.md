---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
Una *referencia de servicio* habilita a un proyecto para obtener acceso a uno o más [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  Use el cuadro de diálogo **Agregar referencia de servicio** para buscar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en la solución actual, localmente, en una red de área local o en Internet.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Agregar una referencia de servicio  
  
#### Para agregar una referencia a un servicio externo  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto al que va a agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.  
  
     Aparecerá el cuadro de diálogo **Agregar referencia de servicio**.  
  
2.  En el cuadro **Dirección**, escriba la dirección URL para el servicio y, a continuación, haga clic en **Ir** para buscar el servicio.  Si el servicio implementa seguridad de nombre de usuario y contraseña, es posible que se solicite un nombre de usuario y una contraseña.  
  
    > [!NOTE]
    >  Solamente debería agregar referencia a servicios desde una fuente de confianza.  Al agregar referencias desde un origen que no es de confianza, puede poner en peligro la seguridad.  
  
     También puede seleccionar la dirección URL de la lista **Dirección**, que almacena las 15 direcciones URL anteriores donde se han encontrado metadatos de servicio válidos.  
  
     Mientras se realiza la búsqueda se muestra una barra de progreso.  Puede detener la búsqueda en cualquier momento haciendo clic en **Detener**.  
  
3.  En la lista **Servicios**, expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.  
  
4.  En el cuadro **Espacio de nombres**, escriba el espacio de nombres que desea usar para obtener la referencia.  
  
5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.  
  
     Se genera un cliente de servicios \(proxy\) y los metadatos que describen el servicio se agregan al archivo app.config.  
  
#### Para agregar una referencia a un servicio en la solución actual  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto al que va a agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.  
  
     Aparecerá el cuadro de diálogo **Agregar referencia de servicio**.  
  
2.  Haga clic en **Detectar**.  
  
     Todos los servicios \([!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] y servicios WCF\) de la solución actual se agregan a la lista **Servicios**.  
  
3.  En la lista **Servicios**, expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.  
  
4.  En el cuadro **Espacio de nombres**, escriba el espacio de nombres que desea usar para obtener la referencia.  
  
5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.  
  
     Se genera un cliente de servicios \(proxy\) y los metadatos que describen el servicio se agregan al archivo app.config.  
  
## Actualizar una referencia de servicio  
 En ocasiones, el Entity Data Model de [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] cambiará.  Cuando esto sucede, se debe actualizar la referencia de servicio.  
  
#### Para actualizar una referencia de servicio  
  
-   En el **Explorador de soluciones**, haga clic con el botón secundario en la referencia de servicio y, a continuación, haga clic en **Actualizar referencia de servicio**.  
  
     Se muestra un cuadro de diálogo de progreso mientras la referencia se actualiza desde su ubicación original, y el cliente de servicios se vuelve a generar para reflejar cualquier cambio en los metadatos.  
  
## Quitar una referencia de servicio  
 Si ya no se usa una referencia de servicio, puede quitarla de su solución.  
  
#### Para quitar una referencia de servicio  
  
-   En el **Explorador de soluciones**, haga clic con el botón secundario en la referencia de servicio y, a continuación, haga clic en **Eliminar**.  
  
     El cliente de servicios se quitará de la solución y los metadatos que describen el servicio se quitarán del archivo app.config.  
  
    > [!NOTE]
    >  Cualquier código que hace referencia a la referencia de servicio se tendrá que quitar manualmente.  
  
## Vea también  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)