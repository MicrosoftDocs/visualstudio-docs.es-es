---
title: "C&#243;mo: Especificar eventos de compilaci&#243;n (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Especificar eventos de compilaci&#243;n (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los eventos de compilación se pueden utilizar para especificar comandos que se ejecuten antes de iniciarse la compilación o al terminarse la compilación.  Los eventos de compilación sólo se ejecutarán si se han alcanzado correctamente dichos puntos en el proceso de compilación.  
  
 Cuando un proyecto se ha generado, los eventos anteriores a la compilación se agregan a un archivo que se denomina PreBuildEvent.bat y los eventos posteriores a la compilación se agregan a un archivo que se denomina PostBuildEvent.bat.  Si desea asegurar la comprobación de errores, agregue sus propios comandos de comprobación de errores a los pasos de compilación.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Cómo especificar eventos anteriores y posteriores a la compilación  
  
#### Para especificar un evento de compilación  
  
1.  En el **Explorador de soluciones**, seleccione el proyecto para el que desee especificar el evento de compilación.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
3.  Seleccione la ficha **Generar eventos**.  
  
4.  En el cuadro **Línea de comandos del evento anterior a la compilación**, especifique la sintaxis del evento de compilación.  
  
    > [!NOTE]
    >  Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.  
  
5.  En el cuadro **Línea de comandos del evento posterior a la compilación**, especifique la sintaxis del evento de compilación.  
  
    > [!NOTE]
    >  Agregue una instrucción `call` delante de todos los comandos posteriores a la compilación que ejecutan archivos .bat.  Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  En el cuadro **Ejecutar el evento posterior a la compilación**, especifique bajo qué condiciones desea ejecutar el evento posterior a la compilación.  
  
    > [!NOTE]
    >  Para agregar una sintaxis larga o seleccionar cualquier macro de compilación en el [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), haga clic en el botón de puntos suspensivos \(**…**\) para mostrar un cuadro de edición.  
  
     La sintaxis de eventos de compilación puede incluir cualquier comando que sea válido en el símbolo del sistema o en un archivo .bat.  El nombre de los archivos de proceso por lotes deberá ir precedido por `call` para garantizar la ejecución de todos los comandos posteriores.  
  
     **Nota**: si el evento previo o posterior a la compilación no se completa correctamente, puede finalizar la compilación haciendo que la acción del evento salga con un código distinto de cero \(0\), que indica una acción correcta.  
  
## Ejemplo: Cómo cambiar la información del manifiesto mediante un evento posterior a la compilación  
 El procedimiento siguiente muestra cómo establecer la versión mínima del sistema operativo en el manifiesto de la aplicación por medio de un comando .exe al que se llama desde un evento posterior a la compilación \(archivo .exe.manifest en el directorio de proyecto\).  La versión mínima del sistema operativo es un número constituido por cuatro partes, como 4.10.0.0.  Para ello, el comando modificará la sección `<dependentOS>` del manifiesto:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### Para crear un comando .exe para cambiar el manifiesto de la aplicación  
  
1.  Cree una aplicación de consola para el comando.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C\#**, haga clic en **Windows** y, a continuación, en la plantilla **Aplicación de consola**.  Asigne al proyecto el nombre `ChangeOSVersionCS`.  
  
3.  En Program.cs, agregue la línea siguiente a las otras instrucciones `using` de la parte superior del archivo:  
  
    ```  
    using System.Xml;  
    ```  
  
4.  En el espacio de nombres `ChangeOSVersionCS`, reemplace la implementación de la clase `Program`con el código siguiente:  
  
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
  
     El comando acepta dos argumentos: la ruta de acceso del manifiesto de la aplicación \(es decir, la carpeta en la que el proceso de compilación crea el manifiesto, normalmente Projectname.publish\) y la nueva versión del sistema operativo.  
  
5.  Compile el proyecto.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
6.  Copie el archivo .exe en un directorio como `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 A continuación, invoque este comando en un evento posterior a la compilación, para modificar el manifiesto de la aplicación.  
  
#### Para invocar un evento posterior a la compilación a fin de modificar el manifiesto de la aplicación  
  
1.  Cree una aplicación para Windows para el proyecto que se va a publicar.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C\#**, haga clic en **Windows** y, a continuación, en la plantilla **Aplicación de Windows Forms**.  Asigne al proyecto el nombre `CSWinApp`.  
  
3.  Con el proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
4.  En el Diseñador de proyectos, busque la página **Publicar** y establezca **Ubicación de publicación** en `C:\TEMP\`.  
  
5.  Publique el proyecto, haciendo clic en **Publicar ahora.**  
  
     Se compilará el archivo de manifiesto y se colocará en `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`.  Para ver el manifiesto, haga clic con el botón secundario del mouse en el archivo, haga clic en **Abrir con**, seleccione **Seleccionar el programa de una lista** y, a continuación, haga clic en **Bloc de notas**.  
  
     Busque el elemento `<osVersionInfo>` en el archivo.  Por ejemplo, la versión podrían ser:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  En el Diseñador de proyectos, haga clic en la ficha **Eventos de compilación** y en el botón **Edición posterior a la compilación**.  
  
7.  En el cuadro **Línea de comandos del evento posterior a la compilación**, escriba el comando siguiente:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Al compilar el proyecto, este comando cambiará la versión mínima del sistema operativo en el manifiesto de la aplicación a 5.1.2600.0.  
  
     Debido a que la macro `$(TargetPath)` expresa la ruta de acceso completa para el ejecutable que se crea, `$(TargetPath)`.manifest especificará el manifiesto de la aplicación creado en el directorio bin.  Al publicarlo, se copiará este manifiesto en la ubicación de publicación que estableció anteriormente.  
  
8.  Publique otra vez el proyecto.  Vaya a la página **Publicar** y haga clic en **Publicar ahora.**  
  
     Vea de nuevo el manifiesto.  Para ver el manifiesto, abra al directorio de publicación, haga clic con el botón secundario en el archivo, haga clic en **Abrir con**, seleccione **Seleccionar el programa de una lista** y, por último, haga clic en **Bloc de notas**.  
  
     La versión indicada debe ser ahora:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## Vea también  
 [Eventos de compilación \(Página, Diseñador de proyectos\) \(C\#\)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Cómo: Especificar eventos de compilación \(Visual Basic\)](../ide/how-to-specify-build-events-visual-basic.md)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)