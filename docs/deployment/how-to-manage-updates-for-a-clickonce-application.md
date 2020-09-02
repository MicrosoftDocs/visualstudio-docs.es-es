---
title: Cómo administrar las actualizaciones de una aplicación ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 534171d9145d0a21fee7f8831e9a6355e6079cbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382359"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Procedimientos para administrar actualizaciones de aplicaciones ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones pueden buscar actualizaciones automáticamente o mediante programación. Como desarrollador, tiene mucha flexibilidad a la hora de especificar Cuándo y cómo se realizan las comprobaciones de actualización, si las actualizaciones son obligatorias y dónde debe buscar actualizaciones la aplicación.

 Puede configurar la aplicación para que compruebe las actualizaciones automáticamente antes de que se inicie la aplicación o a intervalos establecidos después de que se inicie la aplicación. Además, puede especificar una versión mínima requerida; es decir, se instala una actualización si la versión del usuario es anterior a la versión requerida.

 Puede configurar la aplicación para buscar actualizaciones mediante programación en función de un evento como una solicitud de usuario. En el procedimiento "para buscar actualizaciones mediante programación" en este tema se muestra cómo escribiría código que utiliza la <xref:System.Deployment.Application.ApplicationDeployment> clase para buscar actualizaciones en función de un evento.

 También puede implementar la aplicación desde una ubicación y actualizarla desde otra. Vea el procedimiento "para especificar una ubicación de actualización diferente".

 Para obtener más información, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

 El comportamiento de la actualización se administra en el cuadro de diálogo actualizaciones de la **aplicación** , disponible en la página **publicar** del **Diseñador de proyectos.**

### <a name="to-check-for-updates-before-the-application-starts"></a>Para buscar actualizaciones antes de que se inicie la aplicación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **actualizaciones** para abrir el cuadro de diálogo actualizaciones de la **aplicación** .

4. En el cuadro de diálogo actualizaciones de la **aplicación** , asegúrese de que la casilla de **verificación la aplicación debe buscar actualizaciones** está activada.

5. En la sección **elija cuándo debe buscar actualizaciones la aplicación** , seleccione **antes de que se inicie la aplicación**. Esto garantiza que los usuarios conectados a la red siempre ejecuten la aplicación con las actualizaciones más recientes.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Buscar actualizaciones en segundo plano después de iniciar la aplicación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **actualizaciones** para abrir el cuadro de diálogo actualizaciones de la **aplicación** .

4. En el cuadro de diálogo actualizaciones de la **aplicación** , asegúrese de que la casilla **la aplicación debe buscar actualizaciones** está activada.

5. En la **sección elija cuándo debe buscar actualizaciones la aplicación**, seleccione **después de que se inicie la aplicación**. La aplicación se iniciará más rápidamente de esta manera y, a continuación, comprobará si hay actualizaciones en segundo plano y solo notificará al usuario cuando haya una actualización disponible. Una vez instaladas, las actualizaciones no surtirán efecto hasta que se reinicie la aplicación.

6. En la sección **especificación de la frecuencia con la que la aplicación debe buscar actualizaciones** , seleccione **comprobar cada vez que se ejecute la aplicación** (valor predeterminado) o **Compruebe cada** y escriba un número y un intervalo de tiempo.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Para especificar una versión mínima necesaria para la aplicación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **actualizaciones** para abrir el cuadro de diálogo actualizaciones de la **aplicación** .

4. En el cuadro de diálogo actualizaciones de la **aplicación** , asegúrese de que la casilla de **verificación la aplicación debe buscar actualizaciones** está activada.

5. Active la casilla **especificar una versión mínima requerida para esta aplicación** y, a continuación, escriba los números **principal**, **secundario**, de **compilación**y de **revisión** de la aplicación.

### <a name="to-specify-a-different-update-location"></a>Para especificar una ubicación de actualización diferente

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **actualizaciones** para abrir el cuadro de diálogo actualizaciones de la **aplicación** .

4. En el cuadro de diálogo actualizaciones de la **aplicación** , asegúrese de que la casilla de **verificación la aplicación debe buscar actualizaciones** está activada.

5. En el campo **Ubicación de actualización** , escriba la ubicación de actualización con una dirección URL completa, con el formato *http://Hostname/ApplicationName* o una ruta de acceso UNC con el formato * \\ \Server\ApplicationName*, o haga clic en el botón **examinar** para buscar la ubicación de actualización.

### <a name="to-check-for-updates-programmatically"></a>Para buscar actualizaciones mediante programación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **actualizaciones** para abrir el cuadro de diálogo actualizaciones de la **aplicación** .

4. En el cuadro de diálogo actualizaciones de la **aplicación** , asegúrese de que la casilla de **verificación la aplicación debe buscar actualizaciones** está desactivada. (Opcionalmente, puede activar esta casilla para buscar actualizaciones mediante programación y también permitir que el tiempo de ejecución de ClickOnce Compruebe las actualizaciones automáticamente).

5. En el campo **Ubicación de actualización** , escriba la ubicación de actualización con una dirección URL completa, con el formato *http://Hostname/ApplicationName* o una ruta de acceso UNC con el formato * \\ \Server\ApplicationName*, o haga clic en el botón **examinar** para buscar la ubicación de actualización. La ubicación de la actualización es donde la aplicación buscará una versión actualizada de sí mismo.

6. Cree un botón, un elemento de menú u otro elemento de la interfaz de usuario en un Windows Form que los usuarios seleccionarán para buscar actualizaciones. En el controlador de eventos de ese elemento, llame a un método para buscar e instalar actualizaciones. Puede encontrar un ejemplo de código de Visual Basic y Visual C# para este método en [Cómo: buscar actualizaciones de aplicaciones mediante programación con la API de implementación de ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).

7. Compile la aplicación.

## <a name="see-also"></a>Consulte también
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Cuadro de diálogo Actualizaciones de la aplicación](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [Selección de una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Como: buscar actualizaciones de aplicaciones mediante programación con la API de implementación ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
