---
title: "Tutorial: Crear una aplicaci&#243;n b&#225;sica de Shell aislado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell de Visual Studio, tutoriales"
  - "Shell [Visual Studio], tutoriales"
  - "tutoriales [Visual Studio], aislado aplicación shell"
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# Tutorial: Crear una aplicaci&#243;n b&#225;sica de Shell aislado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo crear una solución de shell aislado, personalizar la ventana de ayuda acerca de la herramienta y crear un programa de instalación que instala el shell aislado.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Para implementar el shell aislado, también debe usar el paquete redistribuible de Visual Studio Shell \(aislado\).  
  
## Creación de una solución de Shell aislado  
 Esta sección muestra cómo utilizar la plantilla de proyecto de Visual Studio Shell aislado para crear una solución de shell aislado. La solución contiene los proyectos siguientes:  
  
-   El *SolutionName*. Proyecto de AboutBoxPackage, que le permite personalizar la apariencia de la ayuda\/acerca de cuadro.  
  
-   El proyecto ShellExtensionsVSIX, que contiene el archivo source.extension.vsixmanifest que define los distintos componentes de la aplicación de shell aislado.  
  
-   El *nombresolución* proyecto que genera el archivo ejecutable que llama a la aplicación de shell aislado. Este proyecto contiene la carpeta de la personalización del Shell, que permite personalizar la apariencia y comportamiento de la aplicación de shell aislado.  
  
-   El *nombresolución* proyecto de interfaz de usuario, que genera un ensamblado satélite que define los comandos de menú activo y cadenas localizables.  
  
#### Para crear una solución básica de shell aislado  
  
1.  Abra Visual Studio y cree un nuevo proyecto.  
  
2.  En el **nuevo proyecto** ventana, expanda **otros tipos de proyectos** y, a continuación, **extensibilidad**. Seleccione el **Visual Studio Shell aislado** plantilla de proyecto.  
  
3.  Denomine el proyecto `MyVSShellStub` y especifique una ubicación. Asegúrese de que **Crear directorio para la solución** está activada y, a continuación, haga clic en **Aceptar**.  
  
     Aparece la nueva solución en **el Explorador de soluciones**.  
  
4.  Compile la solución y empezar a depurar la aplicación de shell aislado.  
  
     Visual Studio shell aislado aparece. Lee de la barra de título **MyVSShellStub**. El icono de la barra de título se genera a partir de \\MyVSShellStub\\Resource Files\\ApplicationIcon.ico.  
  
## Personalizar el nombre de la aplicación y el icono  
 Puede personalizar la aplicación con el nombre de su compañía y su logotipo en la barra de título. Los pasos siguientes muestran cómo cambiar el nombre y el icono que se muestran en la barra de título de la aplicación personalizada cambiando el archivo de definición de paquete, MyVSShellStub.Application.pkgdef.  
  
#### Para personalizar el nombre de la aplicación y el icono  
  
1.  En el proyecto MyVSShellStub, abra \\Shell Customization\\MyVSShellStub.Application.pkgdef.  
  
2.  Cambiar el `AppName` al valor del elemento **"AppName" \= "Editor de música de Fabrikam"**  
  
3.  Para cambiar el icono de la aplicación, copie un icono diferente en el directorio \\MyVSShellStub\\MyVSShellStub\\MyVSShellStub\\. Cambie el nombre del archivo de ApplicationIcon.ico existente ApplicationIcon1.ico. Cambie el nombre del nuevo archivo ApplicationIcon.ico.  
  
4.  Compile la solución e iniciar la depuración. El shell aislado aparece el IDE. La barra de título tiene su nuevo icono junto a **Fabrikam música Editor**.  
  
## Personalizar la página de inicio del explorador Web predeterminado  
 Esta sección muestra cómo cambiar la página principal predeterminada de la **explorador Web** ventana cambiando el archivo de definición de paquete.  
  
#### Para personalizar la página principal del explorador Web  
  
1.  En el archivo MyVSShellStub.Application.pkgdef, cambie la `DefaultHomePage` valor del elemento a "http:\/\/www.microsoft.com".  
  
2.  Recompile el proyecto MyVSShellStub.  
  
3.  Compile la solución e iniciar la depuración.  
  
4.  En **vista y otras ventanas**, haga clic en **explorador Web**. El **explorador Web** ventana muestra la página principal de Microsoft Corporation.  
  
## Quitar el comando de impresión  
 El archivo .vsct en un proyecto de la interfaz de usuario de shell aislado consta de un conjunto de declaraciones del formulario `<Define name=No_`*elemento*`>`, donde *elemento* es uno de los comandos y menús estándar de Visual Studio.  
  
 Si no tiene una declaración, menú o el comando se excluye el shell aislado. Por el contrario, si se marca como comentario una declaración, se incluye el menú o el comando en el shell aislado.  
  
 En los pasos siguientes, se quite el comentario de comando de impresión en el archivo .vsct.  
  
#### Para quitar el comando de impresión  
  
1.  Compruebe que la **Imprimir** comando aparece en el **archivo** menú de la aplicación de shell aislado.  
  
2.  En el proyecto MyVSShellStubUI, abra \\Resource Files\\MyVSShellStubUI.vsct para su edición.  
  
3.  Quite el comentario de esta línea:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Esto quita el comando de impresión.  
  
5.  Inicie la depuración de la aplicación de shell aislado. Compruebe que la **archivo \/ imprimir** comando ha desaparecido.  
  
## Quitar características desde el Shell aislado  
 Puede quitar algunos de los paquetes que se cargan con Visual Studio, edite el archivo de .pkgundef si no desea que estas características en la aplicación de shell aislado personalizado. Especifique el paquete en una de las subclaves de la clave de registro $RootKey$ \\Packages.  
  
> [!NOTE]
>  Para obtener las características de los GUID de Visual Studio, consulte [GUID del paquete de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 El siguiente procedimiento muestra cómo quitar el XML editor desde el shell aislado.  
  
#### Para quitar el editor XML  
  
1.  Abra el archivo MyVSShellStub.pkgundef en la carpeta de Shell personalización del proyecto MyVSShellStub.  
  
2.  Quite la línea siguiente:  
  
     \[$RootKey$ \\Packages\\ {87569308\-4813\-40a0\-9cd0\-d7a30838ca3f}\]  
  
3.  Recompile la solución e iniciar la depuración del shell aislado. Abra un archivo XML, por ejemplo, \\MyVSShellStub\\MyVSShellStub\\MyVSShellStubUI\\MyVSShellStubUI.vsct. Compruebe que no se colorea las palabras clave XML en el archivo y que escribe "\<" en una línea no mostrar información sobre herramientas XML.  
  
## Personalización de la ayuda acerca del cuadro  
 Puede personalizar la ayuda\/acerca de cuadro, que se crea como parte de la plantilla de proyecto de shell aislado.  
  
#### Para personalizar el nombre de la empresa  
  
1.  El nombre de la empresa, información de copyright, versión del producto y descripción del producto se encuentran en el proyecto MyVSShellStub.AboutBoxPackage, en el archivo \\Properties\\AssemblyInfo.cs. Abrir este archivo.  
  
2.  Cambiar el `AssemblyCompany` valor a **Fabrikam**, el `AssemblyProduct` y `AssemblyTitle` valores **Fabrikam música Editor**, y el `AssemblyCopyright` valor a **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")] [assembly: AssemblyDescription("")] [assembly: AssemblyConfiguration("")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor ")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Para agregar una descripción del producto, cambie la `AssemblyDescription` valor **la descripción del editor de música de Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Inicie la depuración y en la aplicación de shell aislado, abra el **Ayuda acerca** cuadro. Debería ver las cadenas modificadas. El título de la ayuda\/acerca de cuadro es igual que el `AssemblyTitle` valor en AssemblyInfo.cs.  
  
5.  Las propiedades de la **Ayuda\/acerca de** propio cuadro se encuentran en el archivo MyVSShellStub.AboutBoxPackage\\AboutBox.xaml. Para cambiar el ancho de la ayuda\/acerca de cuadro, vaya a la `AboutDialogStyle` Bloquear y establecer el `Width` propiedad a 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window"> <Setter Property="Height" Value="Auto" /> <Setter Property="Width" Value="200" /> <Setter Property="ShowInTaskbar" Value="False" /> <Setter Property="ResizeMode" Value="NoResize" /> <Setter Property="WindowStyle" Value="SingleBorderWindow" /> <Setter Property="SizeToContent" Value="Height" /> </Style>  
    ```  
  
6.  Recompile la solución e iniciar la depuración del shell aislado. La ayuda sobre el cuadro debe ser aproximadamente cuadrado.  
  
## Antes de implementar la aplicación de Shell aislado  
 La aplicación de shell aislado puede instalarse en cualquier equipo que tenga el paquete redistribuible de Visual Studio Shell \(aislado\). Para obtener más información sobre el paquete redistribuible, vea el [descargas de extensibilidad de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) sitio Web.  
  
## Implementar la aplicación de Shell aislado  
 Implementar la aplicación de shell aislado a un equipo de destino mediante la creación de un proyecto de instalación. Debe especificar estas cosas:  
  
-   El diseño de las carpetas y archivos en el equipo de destino.  
  
-   Las condiciones de inicio que garantizan que .NET Framework y Visual Studio shell en tiempo de ejecución que están instaladas en el equipo de destino.  
  
 En el siguiente procedimiento debe instalar InstallShield Limited Edition en el equipo.  
  
#### Para crear el proyecto de instalación  
  
1.  En **el Explorador de soluciones**, haga clic en el nodo de solución y, a continuación, haga clic en **Agregar nuevo proyecto**.  
  
2.  En el **nuevo proyecto** diálogo cuadro, expanda **otros tipos de proyectos** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield. Nuevo proyecto el nombre `MySetup` y, a continuación, haga clic en **Aceptar**.  
  
3.  Si ya está instalado InstallShield Limited Edition, continúe con el paso siguiente.  
  
     Si no está ya instalado InstallShield Limited Edition, aparece la página de descarga de InstallShield. Siga las instrucciones para descargar e instalar el producto, elegir la versión de InstallShield que sea compatible con su versión de Visual Studio. Debe decidir si desea registrar la instalación de InstallShield o usar como una evaluación. Debe reiniciar Visual Studio después de completar la instalación.  
  
    > [!IMPORTANT]
    >  Debe iniciar Visual Studio como administrador antes de crear un proyecto de InstallShield. Si no lo hace, obtendrá un error al compilar el proyecto.  
  
 Los pasos siguientes muestran cómo configurar el proyecto de instalación.  
  
> [!IMPORTANT]
>  Asegúrese de que ha compilado la configuración release del proyecto de shell aislado de al menos una vez antes de configurar el proyecto de instalación.  
  
#### Para configurar el proyecto de instalación  
  
1.  En el **el Explorador de soluciones**, en el **MySetup** del proyecto, elija **Asistente para proyectos**. En la fila inferior de la **Asistente para proyectos** ventana, elija **información de la aplicación**. Escriba **Fabrikam** como nombre de la compañía y **Fabrikam música Editor** como nombre de la aplicación. Elija la flecha de avance en la parte inferior derecha de la **Asistente para proyectos**.  
  
2.  Seleccione **Sí** en **requiere la aplicación cualquier software esté instalado en el equipo?** y, a continuación, seleccione **paquete completo de Microsoft .NET Framework 4.5**.  
  
3.  Elija la **archivos de la aplicación** situado en la parte inferior de la ventana y asegúrese de que el **Fabrikam música Editor** Seleccionar carpeta.  
  
4.  Elija la **Agregar archivos** botón. En el **Agregar archivos** cuadro de diálogo, agregue los siguientes archivos desde el **MyVSShellStub\\Release** carpeta:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Haga clic en el **Agregar resultados del proyecto** botón y agregue **salida principal MyVSShellStub**. Haga clic en **Aceptar**.  
  
6.  En el panel izquierdo, bajo **equipo de destino**, haga clic en el **Fabrikam música Editor \[INSTALLDIR\]** nodo y agregue un **nueva carpeta** denominado **extensiones de**.  
  
7.  Haga clic en el **extensiones de** en el panel izquierdo y agregue una nueva carpeta denominada **aplicación**.  
  
8.  Seleccione el **aplicación** carpeta y haga clic en el **Agregar resultados del proyecto** a continuación, seleccione el resultado principal del proyecto MyVSShellStub.AboutBoxPackage.  
  
9. Haga clic en el **Agregar archivos** botón y desde la carpeta \\MyVSShellStub\\Release\\Extensions\\Application\\, agregue los siguientes archivos:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Haga clic en el **Fabrikam música Editor \[INSTALLDIR\]** en el panel izquierdo y agregue una nueva carpeta denominada **1033**.  
  
11. Seleccione la carpeta 1033 y, a continuación, haga clic en el **Agregar resultados del proyecto** y seleccione el resultado principal del proyecto MyVSShellStubUI.  
  
12. Mover a la **accesos directos a aplicaciones** ventana.  
  
13. Haga clic en **nuevo** para crear un acceso directo y seleccione **\[ProgramFilesFolder\] \\Fabrikam\\Fabrikam Music Editor\\MyVSShellStub.Primary Output**.  
  
14. Mover a la **entrevista de la instalación** panel.  
  
15. Establece todos los elementos en **No**.  
  
16. En **el Explorador de soluciones**, en el proyecto MySetup, abra **definir los requisitos de instalación y las acciones \\ requisitos**. El **requisitos** se abre la ventana.  
  
17. Haga clic en **requisitos de Software del sistema** y seleccione **Crear nueva condición de inicio**. El **Asistente de búsqueda de sistema** aparece.  
  
18. En el **¿Qué desea buscar?** panel, elija **entrada del registro** en la lista desplegable y haga clic en **siguiente**.  
  
19. En el **cómo desea buscar?** panel, seleccione **HKEY\_LOCAL\_MACHINE** como la raíz del registro. Escriba **SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** para sistemas de 64 bits o **SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** para sistemas de 32 bits y escriba **instalar** como el valor del registro. Haga clic en **Siguiente**.  
  
20. En el **¿Qué desea hacer con el valor?** panel, escriba **este producto requiere Visual Studio 2015 aislado Shell Redistributable instalarse.** como el texto de presentación y haga clic en **Finalizar**.  
  
21. Recompile la solución de shell aislado para crear el proyecto de instalación.  
  
     Puede encontrar el archivo setup.exe en la carpeta siguiente:  
  
     \\MyVSShellStub\\MySetup\\MySetup\\Express\\SingleImage\\DiskImages\\DISK1  
  
## Probar el programa de instalación  
 Para probar el programa de instalación, copie el archivo setup.exe a otro equipo y ejecute el archivo ejecutable de instalación. Debe ser capaz de ejecutar la aplicación de shell aislado.