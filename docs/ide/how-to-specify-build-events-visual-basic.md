---
title: "C&#243;mo: Especificar eventos de compilaci&#243;n (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "eventos de compilación [Visual Studio]"
  - "compilaciones [Visual Studio], eventos"
  - "eventos [Visual Studio], compilaciones"
  - "eventos posteriores a la compilación"
  - "eventos anteriores a la compilación"
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Especificar eventos de compilaci&#243;n (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los eventos de compilación en Visual Basic pueden utilizarse para ejecutar scripts, macros u otras acciones como una parte del proceso de compilación.  Los eventos anteriores a la compilación se producen antes de la compilación; los eventos posteriores a la compilación se producen después de la compilación.  
  
 Los eventos de compilación se especifican en el cuadro de diálogo **Eventos de compilación**, disponible en la página **Compilación** del **Diseñador de proyectos**.  
  
> [!NOTE]
>  Visual Basic Express no admite la entrada de eventos de compilación.  Solo se admite en el producto de Visual Studio completo.  
  
## Cómo especificar eventos anteriores y posteriores a la compilación  
  
#### Para especificar un evento de compilación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Compilar**.  
  
3.  Haga clic en el botón **Eventos de compilación** para abrir el cuadro de diálogo **Eventos de compilación**.  
  
4.  Escriba los argumentos de la línea de comandos para la acción anterior o posterior a la compilación y haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Agregue una instrucción `call` delante de todos los comandos posteriores a la compilación que ejecutan archivos .bat.  Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
    > [!NOTE]
    >  Si el evento previo o posterior a la compilación no se completa correctamente, puede finalizar la compilación haciendo que la acción del evento salga con un código distinto de cero \(0\), que indica una acción correcta.  
  
## Ejemplo: Cómo cambiar la información del manifiesto mediante un evento posterior a la compilación  
 El procedimiento siguiente muestra cómo establecer la versión mínima del sistema operativo en el manifiesto de la aplicación por medio de un comando .exe al que llama un evento posterior a la compilación \(archivo .exe.manifest en el directorio de proyecto\).  La versión mínima del sistema operativo es un número constituido por cuatro partes, como 4.10.0.0.  Para ello, el comando modificará la sección `<dependentOS>` del manifiesto:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### Para crear un comando .exe para cambiar el manifiesto de la aplicación  
  
1.  Cree una aplicación de consola para el comando.  En el menú **Archivo**, seleccione **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en el nodo **Visual Basic**, seleccione **Windows** y, a continuación, la plantilla **Aplicación de consola**.  Asigne al proyecto el nombre `ChangeOSVersionVB`.  
  
3.  En Module1.vb, agregue la línea siguiente a las otras instrucciones `Imports` de la parte superior del archivo:  
  
    ```  
    Imports System.Xml  
    ```  
  
4.  Agregue el código siguiente en `Sub Main`:  
  
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
  
     El comando acepta dos argumentos.  El primer argumento es la ruta de acceso al manifiesto de aplicación \(es decir, la carpeta donde el proceso de compilación crea el manifiesto, que suele ser NombreDelProyecto.publish\).  El segundo argumento es la nueva versión del sistema operativo.  
  
5.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
6.  Copie el archivo .exe en un directorio como `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 A continuación, invoque este comando en un evento posterior a la compilación, para modificar el manifiesto de la aplicación.  
  
#### Para invocar un evento posterior a la compilación a fin de modificar el manifiesto de la aplicación  
  
1.  Cree una aplicación para Windows para el proyecto que se va a publicar.  En el menú **Archivo**, seleccione **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en el nodo **Visual Basic**, seleccione **Windows** y, a continuación, la plantilla **Aplicación para Windows**.  Asigne al proyecto el nombre `VBWinApp`.  
  
3.  Con el proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
4.  En el Diseñador de proyectos, vaya a la página **Publicar** y establezca **Ubicación de publicación** en `C:\TEMP\`.  
  
5.  Publique el proyecto, haciendo clic en **Publicar ahora.**  
  
     Se compilará el archivo de manifiesto y se colocará en `C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest`.  Para ver el manifiesto, haga clic con el botón secundario del mouse en el archivo, y seleccione sucesivamente **Abrir con**, **Seleccionar el programa de una lista** y **Bloc de notas**.  
  
     Busque el elemento `<osVersionInfo>` en el archivo.  Por ejemplo, la versión podrían ser:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  En el Diseñador de proyectos, seleccione la ficha **Compilación** y haga clic en el botón **Eventos de compilación** para abrir el cuadro de diálogo **Eventos de compilación**.  
  
7.  En el cuadro **Línea de comandos del evento posterior a la compilación**, escriba el comando siguiente:  
  
     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Al compilar el proyecto, este comando cambiará la versión mínima del sistema operativo en el manifiesto de la aplicación a 5.1.2600.0.  
  
     La macro `$(TargetPath)` expresa la ruta de acceso completa para el ejecutable creado.  Por consiguiente, $\(TargetPath\).manifest especificará el manifiesto de aplicación creado en el directorio bin.  Al publicarlo, se copiará este manifiesto en la ubicación de publicación que estableció anteriormente.  
  
8.  Publique otra vez el proyecto.  Vaya a la página **Publicar** y haga clic en **Publicar ahora.**  
  
     Vea de nuevo el manifiesto.  Para ver el manifiesto, vaya al directorio de publicación, haga clic con el botón secundario del mouse en el archivo y seleccione sucesivamente **Abrir con**, **Seleccionar el programa de una lista** y **Bloc de notas**.  
  
     La versión indicada debe ser ahora:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## Vea también  
 [Managing Compilation Properties](http://msdn.microsoft.com/es-es/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Cómo: Especificar eventos de compilación \(C\#\)](../ide/how-to-specify-build-events-csharp.md)