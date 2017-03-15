---
title: "C&#243;mo: Administrar actualizaciones de aplicaciones ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "actualizaciones de aplicaciones"
  - "implementación ClickOnce, administrar aplicaciones"
  - "implementación ClickOnce, actualizaciones"
  - "actualizar datos, ClickOnce"
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# C&#243;mo: Administrar actualizaciones de aplicaciones ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pueden buscar actualizaciones automáticamente o mediante programación.  El desarrollador tiene mucha flexibilidad para especificar cuándo y cómo realizar búsquedas de actualizaciones, si éstas son obligatorias, y dónde debe buscarlas la aplicación.  
  
 Puede configurar la aplicación para que busque actualizaciones automáticamente antes de su inicio, o a intervalos definidos después del inicio de la aplicación.  Además, puede especificar una versión mínima necesaria, es decir, que una actualización se instalará solamente si la versión del usuario es inferior a la versión necesaria.  
  
 Puede configurar la aplicación para que busque actualizaciones mediante programación, en función de un evento, como una solicitud del usuario.  En el procedimiento "Para buscar actualizaciones mediante programación" que se incluye a continuación se explica cómo debe escribirse el código que utiliza la clase <xref:System.Deployment.Application.ApplicationDeployment> para buscar actualizaciones en función de un evento.  
  
 También puede implementar la aplicación desde una ubicación y actualizarla desde otra.  Vea el procedimiento "Para especificar una ubicación de actualización diferente".  
  
 Para obtener más información, vea [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 El comportamiento de actualización se administra en el cuadro de diálogo **Actualizaciones de la aplicación**, disponible en la página **Publicar** del **Diseñador de proyectos**.  
  
### Para buscar actualizaciones antes de que se inicie la aplicación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Actualizaciones** para abrir el cuadro de diálogo **Actualizaciones de la aplicación**.  
  
4.  En el cuadro de diálogo **Actualizaciones de la aplicación**, asegúrese de que está activada la casilla **La aplicación debe buscar actualizaciones**.  
  
5.  En la sección **Elegir cuándo debe buscar actualizaciones la aplicación**, seleccione **Antes de que se inicie la aplicación**.  Esto garantiza que los usuarios conectados a la red ejecuten siempre la aplicación con las últimas actualizaciones.  
  
### Para buscar actualizaciones en segundo plano después de que se inicie la aplicación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Actualizaciones** para abrir el cuadro de diálogo **Actualizaciones de la aplicación**.  
  
4.  En el cuadro de diálogo **Actualizaciones de la aplicación**, asegúrese de que está activada la casilla **La aplicación debe buscar actualizaciones**.  
  
5.  En la sección **Elegir cuándo debe la aplicación comprobar si hay actualizaciones**, seleccione **Después de que se inicie la aplicación**.  De este modo, la aplicación se iniciará con mayor rapidez; a continuación, buscará actualizaciones en segundo plano y sólo enviará una notificación al usuario cuando esté disponible una actualización.  Una vez instaladas, las actualizaciones no tendrán efecto hasta que se reinicie la aplicación.  
  
6.  En la sección **Especifique la frecuencia con la que la aplicación buscará actualizaciones**, seleccione **Buscar cada vez que se ejecute la aplicación** \(valor predeterminado\) o **Buscar cada** y escriba un número y un intervalo de tiempo.  
  
### Para especificar una versión necesaria mínima para la aplicación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Actualizaciones** para abrir el cuadro de diálogo **Actualizaciones de la aplicación**.  
  
4.  En el cuadro de diálogo **Actualizaciones de la aplicación**, asegúrese de que está activada la casilla **La aplicación debe buscar actualizaciones**.  
  
5.  Active la casilla **Especifique la versión mínima requerida para esta aplicación** y, a continuación, escriba los números **Mayor**, **Menor**, **Versión de compilación** y **Revisión** para la aplicación.  
  
### Para especificar una ubicación de actualización diferente  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Actualizaciones** para abrir el cuadro de diálogo **Actualizaciones de la aplicación**.  
  
4.  En el cuadro de diálogo **Actualizaciones de la aplicación**, asegúrese de que está activada la casilla **La aplicación debe buscar actualizaciones**.  
  
5.  En el campo **Ubicación de actualizaciones**, escriba la ubicación de las actualizaciones con una dirección URL completa utilizando el formato http:\/\/Nombre de host\/Nombre de aplicación, o bien, una ruta de acceso UNC utilizando el formato \\\\Servidor\\Nombre de aplicación, o haga clic en el botón **Examinar** para ir a la ubicación de las actualizaciones.  
  
### Para buscar actualizaciones mediante programación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Actualizaciones** para abrir el cuadro de diálogo **Actualizaciones de la aplicación**.  
  
4.  En el cuadro de diálogo **Actualizaciones de la aplicación**, asegúrese de que está desactivada la casilla **La aplicación debe buscar actualizaciones**.  \(Asimismo, puede activar esta casilla para buscar actualizaciones mediante programación y permitir que la versión en tiempo de ejecución de ClickOnce busque actualizaciones automáticamente.\)  
  
5.  En el campo **Ubicación de actualizaciones**, escriba la ubicación de las actualizaciones con una dirección URL completa utilizando el formato http:\/\/Nombre de host\/Nombre de aplicación, o bien, una ruta de acceso UNC utilizando el formato \\\\Servidor\\Nombre de aplicación, o haga clic en el botón **Examinar** para ir a la ubicación de las actualizaciones.  La ubicación de actualizaciones es donde la aplicación buscará una versión actualizada de sí misma.  
  
6.  Cree un botón, elemento de menú u otro elemento de la interfaz de usuario en un Windows Form, que los usuarios seleccionarán para buscar actualizaciones.  En el controlador de eventos de ese elemento, llame a un método para buscar e instalar actualizaciones.  Para ver un ejemplo de código de Visual Basic y de Visual C\# para este tipo de métodos, vea [Como: Buscar actualizaciones de aplicaciones mediante programación utilizando la API de implementación de ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Compile la aplicación.  
  
## Vea también  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Application Updates Dialog Box](http://msdn.microsoft.com/es-es/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Como: Buscar actualizaciones de aplicaciones mediante programación utilizando la API de implementación de ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)