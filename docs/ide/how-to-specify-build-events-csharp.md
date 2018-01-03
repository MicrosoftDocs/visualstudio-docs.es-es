---
title: "Cómo: Especificar eventos de compilación (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 1fcba0ef7abec3c8f5d71d34b8ff4e19e047d50b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-build-events-c"></a>Cómo: Especificar eventos de compilación (C#)
Use eventos de compilación para especificar comandos que se ejecutan antes de que se inicie la compilación o después de que esta finalice. Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación.  
  
 Cuando se compila un proyecto, se agregan eventos anteriores a la compilación en un archivo que se denomina PreBuildEvent.bat y posteriores a la compilación en un archivo denominado PostBuildEvent.bat. Si quiere garantizar la comprobación de errores, agregue sus propios comandos de comprobación de errores a los pasos de compilación.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="how-to-specify-pre-build-and-post-build-events"></a>Cómo especificar eventos anteriores y posteriores a la compilación  
  
#### <a name="to-specify-a-build-event"></a>Para especificar un evento de compilación  
  
1.  En el **Explorador de soluciones**, seleccione el proyecto para el que quiere especificar el evento de compilación.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
3.  Seleccione la pestaña **Eventos de compilación**.  
  
4.  En el cuadro **Línea de comandos del evento anterior a la compilación**, especifique la sintaxis del evento de compilación.  
  
    > [!NOTE]
    >  Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.  
  
5.  En el cuadro **Línea de comandos del evento posterior a la compilación**, especifique la sintaxis del evento de compilación.  
  
    > [!NOTE]
    >  Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos .bat. Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  En el cuadro **Ejecutar el evento posterior a la compilación**, especifique en qué condiciones se ejecuta el evento posterior a la compilación.  
  
    > [!NOTE]
    >  Para agregar una sintaxis más larga o para seleccionar cualquier macro de compilación desde el [cuadro de diálogo Línea de comandos del evento anterior/posterior a la compilación](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), haga clic en el botón de puntos suspensivos (**...**) para mostrar un cuadro de edición.  
  
     La sintaxis del evento de compilación puede incluir cualquier comando que sea válido en un símbolo del sistema o en un archivo .bat. El nombre de un archivo por lotes debe ir precedido por `call` para garantizar que todos los comandos posteriores se ejecuten.  
  
     **Nota** Si su evento anterior o posterior a la compilación no se completa correctamente, puede finalizar la compilación haciendo que la acción del evento salga con un código distinto de cero (0), que indica que la acción se ha realizado correctamente.  
  
## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Ejemplo: Cómo cambiar la información del manifiesto con un evento posterior a la compilación  
 En el procedimiento siguiente se muestra cómo establecer la versión de sistema operativo mínima en el manifiesto de aplicación con un comando .exe que se llame desde un evento posterior a la compilación (el archivo de manifiesto .exe en el directorio del proyecto). La versión mínima del sistema operativo es un número de cuatro partes como 4.10.0.0. Para realizar esto, el comando cambiará la sección `<dependentOS>` del manifiesto:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Para crear un comando .exe para cambiar el manifiesto de aplicación  
  
1.  Cree una aplicación de consola para el comando. Desde el menú **Archivo**, pulse **Nuevo** y, después, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#**, haga clic en **Windows** y, después, haga clic en la plantilla **Aplicación de consola**. Dé un nombre al proyecto `ChangeOSVersionCS`.  
  
3.  En Program.cs, agregue la línea siguiente a las demás instrucciones `using` de la parte superior del archivo:  
  
    ```  
    using System.Xml;  
    ```  
  
4.  En el espacio de nombres `ChangeOSVersionCS`, reemplace la implementación de clase `Program` por el código siguiente:  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     El comando toma dos argumentos: la ruta del manifiesto de aplicación (es decir, la carpeta en la que el proceso de compilación crea el manifiesto, normalmente Projectname.publish), y la nueva versión de sistema operativo.  
  
5.  Compile el proyecto. En el menú **Compilar** , haga clic en **Compilar solución**.  
  
6.  Copie el archivo .exe en un directorio como `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 Después, invoque este comando en un evento posterior a la compilación para modificar el manifiesto de aplicación.  
  
#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Para invocar un evento posterior a la compilación para modificar el manifiesto de aplicación  
  
1.  Cree una aplicación Windows para que se publique el proyecto. Desde el menú **Archivo**, pulse **Nuevo** y, después, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#**, haga clic en **Escritorio clásico de Windows** y, después, haga clic en la plantilla **Aplicación de Windows Forms**. Dé un nombre al proyecto `CSWinApp`.  
  
3.  Con el proyecto seleccionado en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Propiedades**.  
  
4.  En el Diseñador de proyectos, busque la página **Publicar** y establezca **Ubicación de publicación** en `C:\TEMP\`.  
  
5.  Publique el proyecto haciendo clic en **Publicar ahora**.  
  
     El archivo de manifiesto se compilará y se colocará en `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`. Para ver el manifiesto, haga clic con el botón derecho en el archivo, haga clic en **Abrir con**, seleccione **Seleccionar el programa de la lista** y, después, haga clic en **Bloc de notas**.  
  
     Busque el archivo para el elemento `<osVersionInfo>`. Por ejemplo, la versión puede ser:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  En el Diseñador de proyectos, haga clic en la pestaña **Eventos de compilación** y haga clic en el botón **Edición posterior a la compilación**.  
  
7.  En el cuadro **Línea de comandos del evento posterior a la compilación**, escriba el comando siguiente:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Cuando compile el proyecto, este comando cambiará la versión mínima del sistema operativo en el manifiesto de aplicación a 5.1.2600.0.  
  
     Como la macro `$(TargetPath)` expresa la ruta de acceso completa del archivo ejecutable que se crea, el manifiesto `$(TargetPath)` especificará el manifiesto de aplicación que se ha creado en el directorio bin. La publicación copiará este manifiesto en la ubicación de publicación que ha establecido anteriormente.  
  
8.  Vuelva a publicar el proyecto. Vaya a la página **Publicar** y haga clic en **Publicar ahora**.  
  
     Vea el manifiesto de nuevo. Para ver el manifiesto, abra el directorio de publicación, haga clic con el botón derecho en el archivo, haga clic en **Abrir con**, seleccione **Seleccionar el programa de la lista** y, después, haga clic en **Bloc de notas**.  
  
     La versión ahora debe leerse:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Eventos de compilación (Página, Diseñador de proyectos) (C#)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Cómo: Especificar eventos de compilación (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)   
 [Compilar y generar en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)