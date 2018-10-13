---
title: 'Cómo: Especificar eventos de compilación (Visual Basic) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c9c6c937d0426170854ef3a9de04348005fc0cd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298901"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Cómo: Especificar eventos de compilación (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los eventos de compilación en Visual Basic se pueden usar para ejecutar scripts, macros u otras acciones como parte del proceso de compilación. Los eventos anteriores a la compilación se producen antes de la compilación; los eventos posteriores a la compilación se producen después de la compilación.  
  
 Los eventos de compilación se especifican en el cuadro de diálogo **Eventos de compilación**, disponible en la página **Compilar** del **Diseñador de proyectos**.  
  
> [!NOTE]
>  Visual Basic Express no admite la entrada de eventos de compilación. Solo se admite en el producto completo de Visual Studio.  
  
## <a name="how-to-specify-pre-build-and-post-build-events"></a>Cómo especificar eventos anteriores y posteriores a la compilación  
  
#### <a name="to-specify-a-build-event"></a>Para especificar un evento de compilación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Compilar**.  
  
3.  Haga clic en el botón **Eventos de compilación** para abrir el cuadro de diálogo **Eventos de compilación**.  
  
4.  Escriba los argumentos de línea de comandos para la acción anterior o posterior a la compilación y después haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos .bat. Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
    > [!NOTE]
    >  Si su evento anterior o posterior a la compilación no se completa correctamente, puede finalizar la compilación haciendo que la acción del evento salga con un código distinto de cero (0), que indica que la acción se ha realizado correctamente.  
  
## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Ejemplo: Cómo cambiar la información del manifiesto con un evento posterior a la compilación  
 En el procedimiento siguiente se muestra cómo establecer la versión de sistema operativo mínima en el manifiesto de aplicación con un comando .exe llamado desde un evento posterior a la compilación (el archivo de manifiesto .exe en el directorio del proyecto). La versión mínima del sistema operativo es un número de cuatro partes como 4.10.0.0. Para realizar esto, el comando cambiará la sección `<dependentOS>` del manifiesto:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Para crear un comando .exe para cambiar el manifiesto de aplicación  
  
1.  Cree una aplicación de consola para el comando. En el menú **Archivo**, haga clic en **Nuevo** y después haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en el nodo **Visual Basic**, seleccione **Windows** y, después, la plantilla **Aplicación de consola**. Dé un nombre al proyecto `ChangeOSVersionVB`.  
  
3.  En Module1.vb, agregue la línea siguiente a las demás instrucciones `Imports` de la parte superior del archivo:  
  
    ```  
    Imports System.Xml  
    ```  
  
4.  Agregue el siguiente código en `Sub Main`:  
  
    ```  
    Sub Main()  
       Dim applicationManifestPath As String  
       applicationManifestPath = My.Application.CommandLineArgs(0)  
       Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)  
  
       'Get version name  
       Dim osVersion As Version  
       If My.Application.CommandLineArgs.Count >= 2 Then  
          osVersion = New Version(My.Application.CommandLineArgs(1).ToString)  
       Else  
          Throw New ArgumentException("OS Version not specified.")  
       End If  
       Console.WriteLine("Desired OS Version: " & osVersion.ToString())  
  
       Dim document As XmlDocument  
       Dim namespaceManager As XmlNamespaceManager  
       namespaceManager = New XmlNamespaceManager(New NameTable())  
       With namespaceManager  
          .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")  
          .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")  
       End With  
  
       document = New XmlDocument()  
       document.Load(applicationManifestPath)  
  
       Dim baseXPath As String  
       baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"  
  
       'Change minimum required OS Version.  
       Dim node As XmlNode  
       node = document.SelectSingleNode(baseXPath, namespaceManager)  
       node.Attributes("majorVersion").Value = osVersion.Major.ToString()  
       node.Attributes("minorVersion").Value = osVersion.Minor.ToString()  
       node.Attributes("buildNumber").Value = osVersion.Build.ToString()  
       node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()  
  
       document.Save(applicationManifestPath)  
    End Sub  
    ```  
  
     El comando toma dos argumentos. El primero es la ruta al manifiesto de aplicación (es decir, la carpeta en la que el proceso de compilación crea el manifiesto, normalmente Projectname.publish). El segundo es la nueva versión del sistema operativo.  
  
5.  En el menú **Compilar** , haga clic en **Compilar solución**.  
  
6.  Copie el archivo .exe en un directorio como `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 Después, invoque este comando en un evento posterior a la compilación para cambiar el manifiesto de aplicación.  
  
#### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Para invocar un evento posterior a la compilación para cambiar el manifiesto de aplicación  
  
1.  Cree una aplicación Windows para que se publique el proyecto. En el menú **Archivo**, haga clic en **Nuevo** y después haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo el **Visual Basic** nodo, seleccione **Windows** y, a continuación, el **aplicación Windows** plantilla. Dé un nombre al proyecto `VBWinApp`.  
  
3.  Con el proyecto seleccionado en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Propiedades**.  
  
4.  En el Diseñador de proyectos, vaya a la página **Publicar** y establezca **Ubicación de publicación** en `C:\TEMP\`.  
  
5.  Publique el proyecto haciendo clic en **Publicar ahora**.  
  
     El archivo de manifiesto se compilará y se colocará en `C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest`. Para ver el manifiesto, haga clic con el botón derecho en el archivo, haga clic en **Abrir con**, seleccione **Select the program from a list** (Seleccionar el programa de la lista) y, después, haga clic en **Bloc de notas**.  
  
     Busque el archivo para el elemento `<osVersionInfo>`. Por ejemplo, la versión puede ser:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  En el Diseñador de proyectos, vaya a la pestaña **Compilar** y haga clic en el botón **Eventos de compilación** para abrir el cuadro de diálogo **Eventos de compilación**.  
  
7.  En el cuadro **Línea de comandos del evento posterior a la compilación**, escriba el comando siguiente:  
  
     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Cuando compile el proyecto, este comando cambiará la versión mínima del sistema operativo en el manifiesto de aplicación a 5.1.2600.0.  
  
     La macro `$(TargetPath)` expresa la ruta de acceso completa del ejecutable que se está creando. Por tanto, $(TargetPath).manifest especificará el manifiesto de aplicación creado en el directorio bin. La publicación copiará este manifiesto en la ubicación de publicación que ha establecido anteriormente.  
  
8.  Vuelva a publicar el proyecto. Vaya a la página **Publicar** y haga clic en **Publicar ahora**.  
  
     Vea el manifiesto de nuevo. Para ver el manifiesto, vaya al directorio de publicación, haga clic con el botón derecho en el archivo, haga clic en **Abrir con**, seleccione **Select the program from a list** (Seleccionar el programa de la lista) y, después, haga clic en **Bloc de notas**.  
  
     La versión ahora debe leerse:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Administrar las propiedades de compilación](http://msdn.microsoft.com/en-us/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Página Compilación, Diseñador de proyectos (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Cómo: Especificar eventos de compilación (C#)](../ide/how-to-specify-build-events-csharp.md)



