---
title: Depurar aplicaciones ClickOnce que usan System. Deployment. Application
description: Obtenga información sobre cómo usar y personalizar las características de implementación avanzadas de ClickOnce mediante el acceso al modelo de objetos de implementación proporcionado por System. Deployment. Application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6a014afff6c26b8cfe8f4f7fae508f78ef5905f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912251"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Depuración de aplicaciones ClickOnce que usan System.Deployment.Application
En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la implementación le permite configurar el modo en que se actualiza una aplicación. Sin embargo, si necesita usar y personalizar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las características de implementación avanzada, deberá tener acceso al modelo de objetos de implementación que proporciona <xref:System.Deployment.Application> . Puede usar las <xref:System.Deployment.Application> API para tareas avanzadas como:

- Crear una opción "actualizar ahora" en la aplicación

- Descargas condicionales a petición de distintos componentes de la aplicación

- Actualizaciones integradas directamente en la aplicación

- Garantizar que la aplicación cliente esté siempre actualizada

  Dado que las <xref:System.Deployment.Application> API solo funcionan cuando una aplicación se implementa con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnología, la única manera de depurarlas es implementar la aplicación mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , asociarla a ella y, a continuación, depurarla. Puede ser difícil adjuntar el depurador lo suficientemente pronto, ya que este código suele ejecutarse cuando la aplicación se inicia y se ejecuta antes de que se pueda adjuntar el depurador. Una solución consiste en colocar interrupciones (o paradas, para proyectos de Visual Basic) antes de que el código de comprobación de la actualización o el código a petición.

  La técnica de depuración recomendada es la siguiente:

1. Antes de empezar, asegúrese de que los archivos de código fuente y símbolos (. pdb) se han archivado.

2. Implemente la versión 1 de la aplicación.

3. Cree una nueva solución en blanco. En el menú **Archivo**, haga clic en **Nuevo** y, a continuación,en **Proyecto**. En el cuadro de diálogo **nuevo proyecto** , abra el nodo **otros tipos de proyectos** y, a continuación, seleccione la carpeta **soluciones de Visual Studio** . En el panel **plantillas** , seleccione **solución en blanco**.

4. Agregue la ubicación de origen archivada a las propiedades de esta nueva solución. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución y luego haga clic en **propiedades**. En el cuadro de diálogo **páginas de propiedades** , seleccione **depurar archivos de código fuente** y, a continuación, agregue el directorio del código fuente archivado. De lo contrario, el depurador encontrará los archivos de código fuente desactualizados, ya que las rutas de acceso del archivo de origen se registran en el archivo. pdb. Si el depurador utiliza archivos de código fuente obsoletos, verá un mensaje que indica que el origen no coincide.

5. Asegúrese de que el depurador puede encontrar los archivos *. pdb* . Si los ha implementado con su aplicación, el depurador los busca automáticamente. Siempre busca primero en el ensamblado en cuestión. De lo contrario, deberá agregar la ruta de acceso de archivo a las **ubicaciones del archivo de símbolos (. pdb)** (para obtener acceso a esta opción, en el menú **herramientas** , haga clic en **Opciones**, abra el nodo **depuración** y haga clic en **símbolos**).

6. Depure lo que ocurre entre las `CheckForUpdate` `Download` / `Update` llamadas al método y.

    Por ejemplo, el código de actualización podría ser el siguiente:

   ```vb
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

8. Intente adjuntar el depurador a la aplicación de la versión 1 cuando descargue una actualización de la versión 2. También puede usar el `System.Diagnostics.Debugger.Break` método o simplemente `Stop` en Visual Basic. Por supuesto, no debe dejar estas llamadas a métodos en el código de producción.

    Por ejemplo, suponga que está desarrollando una aplicación Windows Forms y que tiene un controlador de eventos para este método con la lógica de actualización. Para depurar esto, solo tiene que adjuntar antes de que se presione el botón y, después, establecer un punto de interrupción (Asegúrese de abrir el archivo archivado adecuado y establecer el punto de interrupción allí).

   Use la <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> propiedad para invocar las <xref:System.Deployment.Application> API solo cuando se implementa la aplicación; las API no se deben invocar durante la depuración en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vea también
- <xref:System.Deployment.Application>