---
title: Procedimiento Publicar un proyecto que tiene una configuración regional específica | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c103ca9cec3c7c09a383f6c785b52f3f5c6f6bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928979"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Procedimiento Publicación de un proyecto con una configuración regional específica
No es raro que una aplicación contenga componentes con diferentes configuraciones regionales. En este escenario, crearía una solución con varios proyectos para después publicar diferentes proyectos para cada configuración regional. En este procedimiento se muestra cómo usar una macro para publicar el primer proyecto en una solución usando la configuración regional 'en'. Si quiere intentar este procedimiento con una configuración regional que no sea 'en', asegúrese de establecer `localeString` de manera que coincida con la configuración regional que está usando (por ejemplo, 'de' o 'de-DE').  
  
> [!NOTE]
>  Cuando se usa esta macro, la ubicación de publicación debe ser una dirección URL o un recurso compartido UNC (Convención de nomenclatura universal) válidos. Además, Internet Information Services (IIS) debe estar instalado en el equipo. Para instalar IIS, en el menú **Inicio**, haga clic en **Panel de control**. Haga doble clic en **Agregar o quitar programas**. En **Agregar o quitar programas**, haga clic en **Agregar o quitar componentes de Windows**. En el **Asistente para componentes de Windows**, active la casilla **Internet Information Services (IIS)** en la lista **Componentes**. Haga clic en **Finalizar** para cerrar el asistente.  
  
### <a name="to-create-the-publishing-macro"></a>Para crear la macro de publicación  
  
1.  Para abrir el Explorador de macros, en el menú **Herramientas**, apunte a **Macros** y, a continuación, haga clic en el **Explorador de macros**.  
  
2.  Crear un nuevo módulo de macros. En el Explorador de macros, seleccione **MyMacros**. En el menú **Herramientas**, apunte a **Macros** y, a continuación, haga clic en el **Nuevo módulo de macros**. Dé al módulo el nombre **PublishSpecificCulture**.  
  
3.  En el Explorador de macros, expanda el nodo **MyMacros** y haga doble clic en el módulo **PublishAllProjects** para abrirlo (o, en el menú **Herramientas**, apunte a **Macros** y haga clic en **IDE de macros**).  
  
4.  En el IDE de macros, agregue el siguiente código al módulo, después de las instrucciones `Import`:  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certificate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  Cierre el IDE de macros. El foco volverá a Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Para publicar un proyecto para una configuración regional específica  
  
1.  Para crear un proyecto de Aplicación para Windows de Visual Basic, en el menú **Archivo**, seleccione **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione **Aplicación para Windows** en el nodo **Visual Basic**. Dé al proyecto el nombre *PublishLocales*.  
  
3.  Haga clic en Form1. En la ventana **Propiedades**, en **Diseño**, cambie la propiedad **Idioma** de **(Predeterminado)** a **Inglés**. Cambie la propiedad **Texto** del formulario a **MyForm**.  
  
     Tenga en cuenta que los archivos DLL de recursos localizados no se crean hasta que se necesitan. Por ejemplo, se crean cuando se cambia el texto del formulario o uno de sus controles después de haber especificado la nueva configuración regional.  
  
4.  Publique *PublishLocales* usando el IDE de Visual Studio.  
  
     En el **Explorador de soluciones**, seleccione *PublishLocales*. En el menú **Proyecto**, seleccione **Propiedades**. En el Diseñador de proyectos, en el **publicar** , especifique una ubicación de publicación de **http://localhost/PublishLocales**y, a continuación, haga clic en **publicar ahora**.  
  
     Cuando la página web de publicación aparezca, ciérrela. (En este paso, solo tiene que publicar el proyecto, no tiene que instalarlo).  
  
5.  Publique *PublishLocales* de nuevo invocando la macro en la ventana del símbolo del sistema de Visual Studio. Para ver la ventana de símbolo del sistema, en el **vista** menú, elija **Other Windows** y, a continuación, haga clic en **ventana de comandos**, o bien presione **Ctrl** + **Alt**+**A**. En la ventana de símbolo del sistema, escriba `macros`; Autocompletar proporcionará una lista de macros disponibles. Seleccione la macro siguiente y presione ENTRAR:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Cuando el proceso de publicación se realiza correctamente, generará el mensaje que indica "Publicación realizada correctamente para *PublishLocales\PublishLocales.vbproj*. El idioma de publicación era 'en'". Haga clic en **Aceptar** en el cuadro de mensaje. Cuando la página web de publicación aparezca, haga clic en **Instalar**.  
  
7.  Mire en *C:\Inetpub\wwwroot\PublishLocales\en*. Deberá ver los archivos instalados, como los manifiestos, *setup.exe* y el archivo de la página web de publicación, además del archivo DLL de recursos localizados. De forma predeterminada ClickOnce anexa una extensión *.deploy* a los archivos EXE y DLL; puede quitar esta extensión después de la implementación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Entorno de desarrollo de macros](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))   
 [Ventana Explorador de macros](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))   
 [Cómo: Editar y crear macros mediante programación](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))