---
title: 'Cómo: administrar actualizaciones de una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2346ab8bfcaaaaf2934461e251803fd5920f804b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Cómo: Administrar actualizaciones de aplicaciones ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones pueden buscar actualizaciones automáticamente o mediante programación. Como programador, tiene mucha flexibilidad para especificar cuándo y cómo se realizan comprobaciones de actualización, si éstas son obligatorias y donde la aplicación debe buscar actualizaciones.  
  
 Puede configurar la aplicación para buscar actualizaciones automáticamente antes de iniciar la aplicación o a intervalos establecidos tras iniciar la aplicación. También puede especificar la versión mínima requerida; es decir, se instala una actualización si la versión del usuario es inferior a la versión necesaria.  
  
 Puede configurar la aplicación para buscar actualizaciones mediante programación en función de un evento como una solicitud de usuario. El procedimiento "para buscar actualizaciones mediante programación" en este tema se muestra cómo se escribirá código que usa el <xref:System.Deployment.Application.ApplicationDeployment> clase para buscar actualizaciones en función de un evento.  
  
 También puede implementar su aplicación desde una ubicación y actualizarla desde otra. Consulte el procedimiento "para"especificar una ubicación de actualización diferente.  
  
 Para obtener más información, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Comportamiento de actualización se administra en el **actualizaciones de la aplicación** cuadro de diálogo, disponible en la **publicar** página de la **Diseñador de proyectos.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Para buscar actualizaciones antes de iniciar la aplicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación buscará actualizaciones** casilla está activada.  
  
5.  En el **Elija cuándo debe buscar actualizaciones la aplicación** sección, seleccione **antes de iniciar la aplicación**. Esto garantiza que los usuarios conectados a la red siempre ejecuten la aplicación con las últimas actualizaciones.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Para buscar actualizaciones en segundo plano tras iniciar la aplicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que la casilla de verificación **la aplicación buscará actualizaciones** está seleccionada.  
  
5.  En el **elegir cuándo debe buscar la sección actualizaciones de la aplicación**, seleccione **tras iniciar la aplicación**. La aplicación se iniciará más rápidamente de esta manera, y, a continuación, se buscará actualizaciones en segundo plano y notificar únicamente al usuario cuando hay disponible una actualización. Una vez instalado, las actualizaciones no surtirán efecto hasta que se reinicie la aplicación.  
  
6.  En el **especificar la frecuencia con la que la aplicación buscará actualizaciones** sección, seleccione **comprobar cada vez que se ejecuta la aplicación** (valor predeterminado) o **comprobar cada** y escriba un número e intervalo de tiempo.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Para especificar la versión mínima requerida para la aplicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación buscará actualizaciones** casilla está activada.  
  
5.  Seleccione el **especificar la versión mínima requerida para esta aplicación** casilla de verificación y, a continuación, escriba **principal**, **secundaria**, **crear**y  **Revisión** números de la aplicación.  
  
### <a name="to-specify-a-different-update-location"></a>Para especificar una ubicación de actualización diferentes  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación buscará actualizaciones** casilla está activada.  
  
5.  En el **Actualizar ubicación** , escriba la ubicación de actualización con una dirección URL completa, con el formato http://Hostname/ApplicationName, o una ruta de acceso UNC con el formato \\\Server\ApplicationName o haga clic en el **examinar** botón para buscar la ubicación de actualización.  
  
### <a name="to-check-for-updates-programmatically"></a>Para buscar actualizaciones mediante programación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación buscará actualizaciones** casilla de verificación está desactivada. (Si lo desea, puede seleccionar esta casilla de verificación para comprobar las actualizaciones mediante programación y también permiten el tiempo de ejecución de ClickOnce buscar actualizaciones automáticamente).  
  
5.  En el **Actualizar ubicación** , escriba la ubicación de actualización con una dirección URL completa, con el formato http://Hostname/ApplicationName, o una ruta de acceso UNC con el formato \\\Server\ApplicationName o haga clic en el **examinar** botón para buscar la ubicación de actualización. La ubicación de actualización es donde la aplicación buscará una versión actualizada de sí mismo.  
  
6.  Crear un botón, el elemento de menú u otro elemento de interfaz de usuario en un formulario Windows Forms que seleccionarán los usuarios para buscar actualizaciones. Desde el controlador de eventos de ese elemento, llama a un método para buscar e instalar actualizaciones. Puede encontrar un ejemplo de código de Visual Basic y Visual C# para este tipo de método en [Cómo: comprobar si las actualizaciones de aplicaciones mediante programación con la API de implementación de ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Compile su aplicación.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Cuadro de diálogo de las actualizaciones de aplicación](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Como: Buscar actualizaciones de aplicaciones mediante programación a través de la API de implementación ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)