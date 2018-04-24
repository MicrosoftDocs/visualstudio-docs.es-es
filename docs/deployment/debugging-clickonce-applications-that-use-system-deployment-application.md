---
title: Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30cbf4aab2975b95703c24462604c1a43ed3554c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application
En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación le permite configurar cómo se actualiza una aplicación. Sin embargo, si tiene que usar y personalizar avanzados [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] características de implementación, debe tener acceso al modelo de objeto de implementación proporcionado por <xref:System.Deployment.Application>. Puede usar el <xref:System.Deployment.Application> API para las tareas avanzadas como:  
  
-   Crear una opción "Actualizar ahora" en su aplicación  
  
-   Condicional, descarga a petición de diversos componentes de aplicación  
  
-   Actualizaciones que se integra directamente en la aplicación  
  
-   Para garantizar que la aplicación cliente siempre está actualizada  
  
 Dado que el <xref:System.Deployment.Application> API funcionan sólo cuando se implementa una aplicación con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnología, la única forma de depurarlas consiste en implementar la aplicación mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], conectarse a ella, a continuación, depurarla. Puede ser difícil asociar el depurador lo bastante pronto, porque a menudo se ejecuta este código cuando la aplicación se inicia y se ejecuta antes de que se puede asociar el depurador. Una solución consiste en colocar saltos (o se detiene, para proyectos de Visual Basic) antes de su código de petición o código de comprobación de actualización.  
  
 La técnica de depuración recomendada es la siguiente:  
  
1.  Antes de empezar, asegúrese de que se archivan los archivos de código fuente y símbolos (.pdb).  
  
2.  Implemente la versión 1 de la aplicación.  
  
3.  Cree una nueva solución en blanco. Desde el **archivo** menú, haga clic en **New**, a continuación, **proyecto**. En el **nuevo proyecto** cuadro de diálogo, abra el **otros tipos de proyectos** nodo, a continuación, seleccione la **soluciones de Visual Studio** carpeta. En el **plantillas** panel, seleccione **solución en blanco**.  
  
4.  Agregue la ubicación de origen almacenada a las propiedades de esta nueva solución. En **el Explorador de soluciones**, haga clic en el nodo de soluciones, haga clic en **propiedades**. En el **páginas de propiedades** cuadro de diálogo, seleccione **depurar archivos de código fuente**, a continuación, agregue el directorio del código fuente archivado. En caso contrario, el depurador encontrará los archivos de código fuente obsoletos, ya que las rutas de acceso del archivo de origen se registran en el archivo .pdb. Si el depurador utiliza archivos de código fuente obsoletos, verá un mensaje que indica que no coincide con el origen.  
  
5.  Asegúrese de que el depurador puede encontrar los archivos .pdb. Si se ha implementado con la aplicación, el depurador los encuentra automáticamente. Siempre parece junto al ensamblado en cuestión en primer lugar. En caso contrario, debe agregar la ruta de acceso de archivo para el **símbolos ubicaciones del archivo (.pdb)** (para tener acceso a esta opción desde la **herramientas** menú, haga clic en **opciones**, a continuación, abra el  **Depuración** nodo y haga clic en **símbolos**).  
  
6.  Depure lo que sucede entre el `CheckForUpdate` y `Download` / `Update` llamadas al método.  
  
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
  
7.  Implemente la versión 2.  
  
8.  Error al intentar adjuntar al depurador a la aplicación de la versión 1 como descarga una actualización para la versión 2. También puede usar el `System.Diagnostics.Debugger.Break` método o simplemente `Stop` en Visual Basic. Por supuesto, no debe dejar estas llamadas al método en el código de producción.  
  
     Por ejemplo, suponga que está desarrollando una aplicación de formularios Windows Forms, y tiene un controlador de eventos para este método con la lógica de actualización en él. Para depurar este problema, basta con adjuntar antes de que el botón se presiona, establezca un punto de interrupción (asegúrese de que se abra el archivo de almacenamiento adecuado y establece el punto de interrupción en él).  
  
 Use la <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> propiedad que se va a invocar la <xref:System.Deployment.Application> API solo cuando se implementa la aplicación; la API no se deben invocar durante la depuración en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application>