---
title: 'Cómo: Especificar eventos de compilación (C#)'
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 134a5b7cd4bb0ffc9c00a41df12ed196dd2a9212
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115126"
---
# <a name="how-to-specify-build-events-c"></a>Cómo: Especificar eventos de compilación (C#)

Use eventos de compilación para especificar comandos que se ejecutan antes de que se inicie la compilación o después de que esta finalice. Los eventos de compilación solo se ejecutan si se alcanzan correctamente esos puntos en el proceso de compilación.

Cuando se compila un proyecto, los eventos anteriores a la compilación se agregan en un archivo denominado *PreBuildEvent.bat* y los eventos posteriores a la compilación se agregan en un archivo denominado *PostBuildEvent.bat*. Si quiere garantizar la comprobación de errores, agregue sus propios comandos de comprobación de errores a los pasos de compilación.

## <a name="specify-a-build-event"></a>Especificación de un evento de compilación

1. En el **Explorador de soluciones**, seleccione el proyecto para el que quiere especificar el evento de compilación.

2. En el menú **Proyecto**, haga clic en **Propiedades**.

3. Seleccione la pestaña **Eventos de compilación**.

4. En el cuadro **Línea de comandos del evento anterior a la compilación**, especifique la sintaxis del evento de compilación.

   > [!NOTE]
   > Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.

5. En el cuadro **Línea de comandos del evento posterior a la compilación**, especifique la sintaxis del evento de compilación.

   > [!NOTE]
   > Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos *.bat*. Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

6. En el cuadro **Ejecutar el evento posterior a la compilación**, especifique en qué condiciones se ejecuta el evento posterior a la compilación.

   > [!NOTE]
   > Para agregar una sintaxis más larga o para seleccionar cualquier macro de compilación desde el [cuadro de diálogo Línea de comandos del evento anterior/posterior a la compilación](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), haga clic en el botón de puntos suspensivos ( **...** ) para mostrar un cuadro de edición.

   La sintaxis del evento de compilación puede incluir cualquier comando que sea válido en un símbolo del sistema o en un archivo *.bat*. El nombre de un archivo por lotes debe ir precedido por `call` para garantizar que todos los comandos posteriores se ejecuten.

   > [!NOTE]
   > Si su evento anterior o posterior a la compilación no se completa correctamente, puede finalizar la compilación haciendo que la acción del evento salga con un código distinto de cero (0), que indica que la acción se ha realizado correctamente.

## <a name="example"></a>Ejemplo

En el procedimiento siguiente se muestra cómo establecer la versión de sistema operativo mínima en el manifiesto de aplicación con un comando *.exe* que se llame desde un evento posterior a la compilación (el archivo *.exe.manifest* en el directorio del proyecto). La versión mínima del sistema operativo es un número de cuatro partes como 4.10.0.0. Para establecer la versión mínima del sistema operativo, el comando cambiará la sección `<dependentOS>` del manifiesto:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Creación de un comando .exe para cambiar el manifiesto de aplicación

1. Cree un proyecto **Aplicación de consola** para el comando. Asigne al proyecto el nombre **ChangeOSVersionCS**.

2. En *Program.cs*, agregue la línea siguiente a las demás directivas `using` de la parte superior del archivo:

   ```csharp
   using System.Xml;
   ```

3. En el espacio de nombres `ChangeOSVersionCS`, reemplace la implementación de clase `Program` por el código siguiente:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
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

   El comando toma dos argumentos: la ruta del manifiesto de aplicación (es decir, la carpeta en la que el proceso de compilación crea el manifiesto, normalmente *Projectname.publish*), y la nueva versión de sistema operativo.

4. Compile el proyecto.

5. Copie el archivo *.exe* en un directorio, por ejemplo, *C:\TEMP\ChangeOSVersionVB.exe*.

Después, invoque este comando en un evento posterior a la compilación para modificar el manifiesto de aplicación.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Invocación de un evento posterior a la compilación para modificar el manifiesto de aplicación

1. Cree un proyecto **Aplicación de Windows Forms** y asígnele el nombre **CSWinApp**.

2. Con el proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto**, elija **Propiedades**.

3. En el **Diseñador de proyectos**, busque la página **Publicar** y establezca **Ubicación de publicación** en *C:\TEMP*.

4. Publique el proyecto haciendo clic en **Publicar ahora**.

   El archivo de manifiesto se compila y se guarda en *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Para ver el manifiesto, haga clic con el botón derecho en el archivo, haga clic en **Abrir con**, seleccione **Seleccionar el programa de la lista** y, después, haga clic en **Bloc de notas**.

   Busque el archivo para el elemento `<osVersionInfo>`. Por ejemplo, la versión puede ser:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. En el **Diseñador de proyectos**, haga clic en la pestaña **Eventos de compilación** y luego, en **Edición posterior a la compilación**.

6. En el cuadro **Línea de comandos del evento posterior a la compilación**, escriba el comando siguiente:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Al compilar el proyecto, este comando cambiará la versión mínima del sistema operativo en el manifiesto de aplicación a 5.1.2600.0.

   Como la macro `$(TargetPath)` expresa la ruta de acceso completa del archivo ejecutable que se crea, `$(TargetPath).manifest` especifica el manifiesto de aplicación que se ha creado en el directorio *bin*. La publicación copiará este manifiesto en la ubicación de publicación que ha establecido anteriormente.

7. Vuelva a publicar el proyecto.

   La versión del manifiesto debe ahora indicar:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Vea también

- [Página Eventos de compilación, (Diseñador de proyectos) (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Cómo: Especificar eventos de compilación (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
