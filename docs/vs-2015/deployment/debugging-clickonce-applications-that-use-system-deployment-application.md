---
title: Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4a97fb2db4c252efcb2f980915062861933a242e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890314"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación le permite configurar cómo se actualiza una aplicación. Sin embargo, si tiene que usar y personalizar avanzados [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] características de implementación, deberá obtener acceso al modelo de objeto implementación proporcionado por <xref:System.Deployment.Application>. Puede usar el <xref:System.Deployment.Application> API para las tareas avanzadas, como:  
  
- Creación de una opción "Actualizar ahora" en la aplicación  
  
- Descargas de condicional, y a petición de diversos componentes de aplicación  
  
- Actualizaciones que se integra directamente en la aplicación  
  
- Lo que garantiza que la aplicación cliente siempre está actualizada  
  
  Dado que el <xref:System.Deployment.Application> API funcionan sólo cuando se implementa una aplicación con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnología, que es la única manera de depurarlas implementar la aplicación mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], asocie a ella y luego depurarlo. Puede ser difícil asociar el depurador lo bastante pronto, porque a menudo se ejecuta este código cuando la aplicación se inicia y se ejecuta antes de que puede asociar el depurador. Una solución consiste en colocar saltos (o se detiene, los proyectos de Visual Basic) antes de su código de comprobación de actualización o el código y a petición.  
  
  La técnica recomendada de depuración es como sigue:  
  
1. Antes de empezar, asegúrese de que se archivan los archivos de código fuente y símbolos (.pdb).  
  
2. Implemente la versión 1 de la aplicación.  
  
3. Crear una nueva solución en blanco. Desde el **archivo** menú, haga clic en **New**, a continuación, **proyecto**. En el **nuevo proyecto** cuadro de diálogo, abra el **otros tipos de proyectos** nodo, a continuación, seleccione el **soluciones de Visual Studio** carpeta. En el **plantillas** panel, seleccione **solución en blanco**.  
  
4. Agregue la ubicación de archivado de origen a las propiedades de esta nueva solución. En **el Explorador de soluciones**, haga clic en el nodo de solución y luego haga clic en **propiedades**. En el **páginas de propiedades** cuadro de diálogo, seleccione **depurar archivos de código fuente**, a continuación, agregue el directorio del código fuente archivado. En caso contrario, el depurador encontrará los archivos de código fuente obsoletos, ya que las rutas de acceso del archivo de origen se registran en el archivo PDB. Si el depurador utiliza archivos de código fuente obsoletos, verá un mensaje que le indica que no coincide con el origen.  
  
5. Asegúrese de que el depurador puede encontrar los archivos .pdb. Si se ha implementado con la aplicación, el depurador los encontrará automáticamente. Siempre parece junto al ensamblado en cuestión en primer lugar. En caso contrario, deberá agregar la ruta de acceso de almacenamiento para el **ubicaciones de archivo (.pdb) de símbolos** (para tener acceso a esta opción, desde el **herramientas** menú, haga clic en **opciones**, a continuación, abra el  **Depuración** nodo y haga clic en **símbolos**).  
  
6. Depurar lo que sucede entre el `CheckForUpdate` y `Download` / `Update` llamadas al método.  
  
    Por ejemplo, el código de actualización podría ser como sigue:  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Implemente la versión 2.  
  
8. Error al intentar adjuntar al depurador a la aplicación de la versión 1 como descarga una actualización para la versión 2. También puede usar el `System.Diagnostics.Debugger.Break` método o simplemente `Stop` en Visual Basic. Por supuesto, no debe dejar estas llamadas al método en código de producción.  
  
    Por ejemplo, supongamos que está desarrollando una aplicación de Windows Forms, y tiene un controlador de eventos para este método con la lógica de actualización en él. Para depurar esto, simplemente asocie antes de que se presiona el botón y luego establezca un punto de interrupción (asegúrese de que abra el archivo almacenado adecuado y establecer el punto de interrupción).  
  
   Use la <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> propiedad para invocar el <xref:System.Deployment.Application> API solo cuando se implementa la aplicación; las API no deben invocarse durante la depuración en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application>



