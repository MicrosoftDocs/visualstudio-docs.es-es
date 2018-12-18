---
title: 'Cómo: administrar actualizaciones de una aplicación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bd9d8d7e88bc9ee8c8b041571ddaa258067c300
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283657"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Cómo: administrar las actualizaciones de una aplicación ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones pueden buscar actualizaciones automáticamente o mediante programación. Como desarrollador, tiene mucha flexibilidad para especificar cuándo y cómo se realizan comprobaciones de actualización, si éstas son obligatorias y donde la aplicación debe buscar actualizaciones.  
  
 Puede configurar la aplicación para buscar actualizaciones automáticamente antes de se inicia la aplicación o a intervalos establecidos tras iniciar la aplicación. Además puede especificar la versión mínima requerida; es decir, se instala una actualización si la versión del usuario es inferior a la versión necesaria.  
  
 Puede configurar la aplicación para comprobar las actualizaciones mediante programación en función de un evento como una solicitud de usuario. El procedimiento "para buscar actualizaciones mediante programación" en este tema se muestra cómo podría escribir código que usa el <xref:System.Deployment.Application.ApplicationDeployment> clase para comprobar si hay actualizaciones en función de un evento.  
  
 También puede implementar su aplicación desde una ubicación y actualizarla desde otra. Consulte el procedimiento "para"especificar una ubicación de actualización diferente.  
  
 Para obtener más información, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Comportamiento de actualización se administra en el **actualizaciones de la aplicación** cuadro de diálogo, disponible desde el **publicar** página de la **Diseñador de proyectos.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Comprobar si hay actualizaciones antes de iniciar la aplicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** botón para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación debe buscar actualizaciones** casilla está activada.  
  
5.  En el **Elija cuándo debe buscar actualizaciones la aplicación** sección, seleccione **antes de iniciar la aplicación**. Esto garantiza que los usuarios conectados a la red siempre ejecutan la aplicación con las últimas actualizaciones.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Para comprobar las actualizaciones en segundo plano una vez iniciada la aplicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** botón para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que la casilla de verificación **la aplicación debe buscar actualizaciones** está seleccionada.  
  
5.  En el **Elija cuándo debe buscar la aplicación para la sección actualizaciones**, seleccione **tras iniciar la aplicación**. La aplicación se iniciará más rápidamente de esta manera, y, a continuación, se buscan actualizaciones en segundo plano y solo notifica al usuario cuando hay disponible una actualización. Una vez instalado, las actualizaciones no surtirán efecto hasta que se reinicie la aplicación.  
  
6.  En el **especificar con qué frecuencia debe buscar actualizaciones la aplicación** sección, seleccione **comprobar cada vez que se ejecuta la aplicación** (valor predeterminado) o **comprobar cada** y escriba un número e intervalo de tiempo.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Para especificar una versión mínima requerida para la aplicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** botón para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación debe buscar actualizaciones** casilla está activada.  
  
5.  Seleccione el **especifique una versión mínima requerida para esta aplicación** casilla de verificación y, a continuación, escriba **principales**, **menores**, **compilar**y  **Revisión** números de la aplicación.  
  
### <a name="to-specify-a-different-update-location"></a>Para especificar una ubicación de actualización diferente  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** botón para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación debe buscar actualizaciones** casilla está activada.  
  
5.  En el **Actualizar ubicación** , introduzca la ubicación de actualización con una dirección URL completa, con el formato *http://Hostname/ApplicationName*, o una ruta UNC con el formato  *\\\Server\ ApplicationName*, o haga clic en el **examinar** botón para buscar la ubicación de actualización.  
  
### <a name="to-check-for-updates-programmatically"></a>Para comprobar las actualizaciones mediante programación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **actualizaciones** botón para abrir el **actualizaciones de la aplicación** cuadro de diálogo.  
  
4.  En el **actualizaciones de la aplicación** diálogo cuadro, asegúrese de que el **la aplicación debe buscar actualizaciones** casilla está desactivada. (Si lo desea, puede seleccionar esta casilla para comprobar las actualizaciones mediante programación y también permiten el tiempo de ejecución de ClickOnce comprobación automática de actualizaciones).  
  
5.  En el **Actualizar ubicación** , introduzca la ubicación de actualización con una dirección URL completa, con el formato *http://Hostname/ApplicationName*, o una ruta UNC con el formato  *\\\Server\ ApplicationName*, o haga clic en el **examinar** botón para buscar la ubicación de actualización. La ubicación de actualización es donde la aplicación buscará una versión actualizada de sí mismo.  
  
6.  Crear un botón, el elemento de menú o el otro elemento de interfaz de usuario en un formulario de Windows que se seleccionarán los usuarios para comprobar si hay actualizaciones. Desde el controlador de eventos de ese elemento, llame a un método para buscar e instalar las actualizaciones. Puede encontrar un ejemplo de código de Visual Basic y Visual C# para este tipo de método en [Cómo: buscar actualizaciones de aplicaciones mediante programación con la API de implementación ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Compile la aplicación.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Cuadro de diálogo de las actualizaciones de aplicación](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Cómo: buscar actualizaciones de aplicaciones mediante programación con la API de implementación de ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)