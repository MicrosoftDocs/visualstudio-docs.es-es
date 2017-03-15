---
title: "Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, depurar"
  - "depurar, aplicaciones ClickOnce"
  - "depurar, System.Deployment"
  - "implementar aplicaciones [ClickOnce], depurar"
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] permite configurar cómo se actualiza una aplicación.  Sin embargo, si necesita utilizar y personalizar características avanzadas de implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], deberá tener acceso al modelo de objetos de implementación proporcionado por <xref:System.Deployment.Application>.  Puede utilizar las API de <xref:System.Deployment.Application> para tareas avanzadas como:  
  
-   Crear una opción "Actualizar ahora" en su aplicación  
  
-   Descargas condicionales a petición de diversos componentes de aplicación  
  
-   Actualizaciones directamente integradas en la aplicación  
  
-   Garantía de que la aplicación cliente siempre está actualizada  
  
 Dado que las API de <xref:System.Deployment.Application> sólo funcionan cuando una aplicación se implementa con tecnología [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la única forma de depurarlas es implementar la aplicación con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], asociarlas con ella y, a continuación, depurar.  Puede ser difícil asociar el depurador lo bastante pronto, ya que este código se ejecuta con frecuencia al iniciarse la aplicación y antes de poder asociar el depurador.  Una solución es colocar interrupciones \(o detenciones, para los proyectos de Visual Basic\) antes de que actualice el código de comprobación o a petición.  
  
 La técnica de depuración recomendada es la siguiente:  
  
1.  Antes de empezar, asegúrese de que están almacenados los archivos de símbolos \(.pdb\) y de código fuente.  
  
2.  Implemente la versión 1 de la aplicación.  
  
3.  Cree una nueva solución en blanco.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, en **Proyecto**.  En el cuadro de diálogo **Nuevo proyecto**, abra el nodo **Otros tipos de proyectos** y, a continuación, seleccione la carpeta **Soluciones de Visual Studio**.  En el panel **Plantillas**, seleccione **Solución en blanco**.  
  
4.  Agregue la ubicación de origen almacenada a las propiedades de esta nueva solución.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución y, a continuación, haga clic en **Propiedades**.  En el cuadro de diálogo **Páginas de propiedades**, seleccione **Depurar archivos de código fuente** y, a continuación, agregue el directorio del código fuente archivado.  De lo contrario, el depurador encontrará los archivos de código fuente obsoletos, ya que las rutas de acceso del archivo de código fuente están registradas en el archivo .pdb.  Si el depurador utiliza archivos de código fuente obsoletos, verá un mensaje que le indica que el origen no coincide.  
  
5.  Asegúrese de que el depurador puede encontrar los archivos .pdb.  Si los ha implementado con su aplicación, el depurador los encuentra automáticamente.  Siempre busca primero junto al ensamblado en cuestión.  De lo contrario, deberá agregar la ruta de acceso al archivo en **Ubicaciones del archivo de símbolos \(.pdb\)** \(para tener acceso a esta opción, en el menú **Herramientas**, haga clic en **Opciones**, abra el nodo **Depuración** y haga clic en **Símbolos**\).  
  
6.  Depure lo que sucede entre las llamadas a los métodos `CheckForUpdate` y `Download`\/`Update`.  
  
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
  
8.  Intente adjuntar el depurador a la aplicación de la versión 1 mientras descarga una actualización para la versión 2.  Asimismo, puede usar el método `System.Diagnostics.Debugger.Break` o simplemente `Stop` en Visual Basic.  Evidentemente, no debe dejar estas llamadas al método en el código de producción.  
  
     Por ejemplo, supongamos que está desarrollando una aplicación de Windows Forms y tiene un controlador de eventos para este método con lógica de actualización.  Para depurarlo, asocie antes de presionar el botón y establezca un punto de interrupción \(asegúrese de abrir el archivo almacenado adecuado y de establecer el punto de interrupción en él\).  
  
 Utilice la propiedad <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> para invocar las API de <xref:System.Deployment.Application> sólo cuando se implementa la aplicación; las API nunca deben invocarse durante la depuración en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 <xref:System.Deployment.Application>