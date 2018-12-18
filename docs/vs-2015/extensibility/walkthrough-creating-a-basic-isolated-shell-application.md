---
title: 'Tutorial: Crear un Basic aislado aplicación del Shell | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 901bbf12c9c1d153b84b3ed74f6ae8e97ebb2c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777323"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Tutorial: Crear una aplicación básica de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial muestra cómo crear una solución de shell aislado, personalizar la ventana de herramientas Ayuda-acerca y crear un programa de instalación que instala el shell aislado.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md). Para implementar el shell aislado, también debe usar el paquete redistribuible de Visual Studio Shell (aislado).  
  
## <a name="creating-an-isolated-shell-solution"></a>Creación de una solución de Shell aislado  
 En esta sección se muestra cómo usar la plantilla de proyecto de Visual Studio Shell aislado para crear una solución de shell aislado. La solución contiene los proyectos siguientes:  
  
-   El *SolutionName*. Proyecto de AboutBoxPackage, que le permite personalizar la apariencia de la ayuda/acerca de la casilla.  
  
-   El proyecto ShellExtensionsVSIX, que contiene el archivo source.extension.vsixmanifest que define los distintos componentes de la aplicación de shell aislado.  
  
-   El *SolutionName* proyecto, que genera el archivo ejecutable que llama a la aplicación de shell aislado. Este proyecto contiene la carpeta de personalización del Shell, que le permite personalizar la apariencia y comportamiento de la aplicación de shell aislado.  
  
-   El *SolutionName* proyecto de interfaz de usuario, que genera un ensamblado satélite que define cadenas localizables y los comandos de menú activo.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Para crear una solución básica de shell aislado  
  
1.  Abra Visual Studio y cree un nuevo proyecto.  
  
2.  En el **nuevo proyecto** ventana, expanda **otros tipos de proyectos** y, a continuación, **extensibilidad**. Seleccione el **Visual Studio Shell aislado** plantilla de proyecto.  
  
3.  Denomine el proyecto `MyVSShellStub` y especifique una ubicación. Asegúrese de que **crear directorio para la solución** está activada y, a continuación, haga clic en **Aceptar**.  
  
     Aparece la nueva solución en **el Explorador de soluciones**.  
  
4.  Compile la solución y empiece a depurar la aplicación de shell aislado.  
  
     Aparece el shell aislado de Visual Studio. Lee de la barra de título **MyVSShellStub**. El icono de la barra de título se genera desde \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personalizar el nombre de la aplicación y el icono  
 Es posible que desee personalizar la marca de la aplicación con el nombre de su empresa y su logotipo en la barra de título. Los pasos siguientes muestran cómo cambiar el nombre y el icono que se muestran en la barra de título de la aplicación personalizada, cambie el archivo de definición de paquete, MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Para personalizar el nombre de la aplicación y el icono  
  
1.  En el proyecto MyVSShellStub, abra \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Cambiar el `AppName` al valor del elemento **"AppName" = "Editor de música de Fabrikam"**  
  
3.  Para cambiar el icono de aplicación, copie un icono diferente en el directorio \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Cambie el nombre del archivo ApplicationIcon.ico existente ApplicationIcon1.ico. Cambie el nombre del nuevo archivo ApplicationIcon.ico.  
  
4.  Compile la solución y comience la depuración. El shell aislado aparece el IDE. La barra de título tiene el nuevo icono junto a las palabras **Fabrikam música Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personalizar la página de inicio del explorador Web predeterminado  
 En esta sección se muestra cómo cambiar la página principal predeterminada de la **explorador Web** ventana cambiando el archivo de definición de paquete.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Para personalizar la página principal del explorador Web predeterminado  
  
1. En el archivo MyVSShellStub.Application.pkgdef, cambie el `DefaultHomePage` al valor del elemento "<http://www.microsoft.com>".  
  
2. Recompile el proyecto MyVSShellStub.  
  
3. Compile la solución y comience la depuración.  
  
4. En **vista / Windows otras**, haga clic en **explorador Web**. El **explorador Web** ventana muestra la página principal de Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Quitar el comando de impresión  
 El archivo .vsct en un proyecto de interfaz de usuario del shell aislado consta de un conjunto de declaraciones del formulario `<Define name=No_` *elemento*`>`, donde *elemento* es uno de los menús de Visual Studio estándares y comandos.  
  
 Si una declaración es la marca de comentario, ese menú o el comando se excluye del shell aislado. Por el contrario, si se ha convertido en una declaración, el menú o comando se incluye en el shell aislado.  
  
 En los pasos siguientes, se quite el comentario de comando de impresión en el archivo .vsct.  
  
#### <a name="to-remove-the-print-command"></a>Para quitar el comando de impresión  
  
1.  Compruebe que la **impresión** comando aparece en el **archivo** menú de la aplicación de shell aislado.  
  
2.  En el proyecto MyVSShellStubUI, abra \Resource Files\MyVSShellStubUI.vsct para su edición.  
  
3.  Quite esta línea:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Esto quita el comando de impresión.  
  
5.  Empiece a depurar la aplicación de shell aislado. Compruebe que la **archivo / imprimir** comando ha desaparecido.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Quitar características desde el Shell aislado  
 Puede quitar algunos de los paquetes que se cargan con Visual Studio editando el archivo .pkgundef si no desea que esas características en la aplicación de shell aislado personalizado. Especifique el paquete en una de las subclaves de la clave del registro de $RootKey$ \Packages.  
  
> [!NOTE]
>  Para obtener las características de los GUID de Visual Studio, consulte [paquete GUID de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 El siguiente procedimiento muestra cómo quitar el código XML editor desde el shell aislado.  
  
#### <a name="to-remove-the-xml-editor"></a>Para quitar el editor XML  
  
1.  Abra el archivo MyVSShellStub.pkgundef en la carpeta de personalización de Shell del proyecto MyVSShellStub.  
  
2.  Elimine la línea siguiente:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Recompile la solución e iniciar la depuración del shell aislado. Abra un archivo XML, por ejemplo, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Compruebe que no se colorean las palabras clave XML en el archivo y que escriba "<" en una línea no revele información sobre herramientas XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personalización de la ayuda/acerca de la casilla  
 Puede personalizar la ayuda/acerca de cuadro, que se crea como parte de la plantilla de proyecto de shell aislado.  
  
#### <a name="to-customize-the-company-name"></a>Para personalizar el nombre de la empresa  
  
1.  El nombre de la empresa, información de copyright, versión del producto y descripción del producto se encuentran en el proyecto MyVSShellStub.AboutBoxPackage, en el archivo \Properties\AssemblyInfo.cs. Abra este archivo.  
  
2.  Cambio el `AssemblyCompany` valor **Fabrikam**, el `AssemblyProduct` y `AssemblyTitle` valores **Fabrikam música Editor**y el `AssemblyCopyright` valor **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Para agregar una descripción del producto, cambie el `AssemblyDescription` valor **la descripción del editor de música de Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Inicie la depuración y en la aplicación de shell aislado, abra el **ayuda / acerca** cuadro. Debería ver las cadenas modificadas. El título de la ayuda/acerca de la casilla es el mismo que el `AssemblyTitle` valor en AssemblyInfo.cs.  
  
5.  Las propiedades de la **ayuda/acerca** propio cuadro se encuentran en el archivo MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Para cambiar el ancho de la ayuda/acerca de cuadro, vaya a la `AboutDialogStyle` bloquear y establezca el `Width` propiedad a 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Recompile la solución e iniciar la depuración del shell aislado. La ayuda/acerca de cuadro debe ser aproximadamente cuadrado.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Antes de implementar la aplicación de Shell aislado  
 La aplicación de shell aislado puede instalarse en cualquier equipo que tenga el paquete redistribuible de Visual Studio Shell (aislado). Para obtener más información sobre el paquete redistribuible, vea el [descargas de Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sitio Web.  
  
## <a name="deploying-the-isolated-shell-application"></a>Implementar la aplicación de Shell aislado  
 Implementar la aplicación de shell aislado en un equipo de destino mediante la creación de un proyecto de instalación. Debe especificar estas cosas:  
  
- El diseño de las carpetas y archivos en el equipo de destino.  
  
- Las condiciones de inicio que garantizan que .NET Framework y Visual Studio shell en tiempo de ejecución que se instalan en el equipo de destino.  
  
  En el siguiente procedimiento deberá instalar InstallShield Limited Edition en el equipo.  
  
#### <a name="to-create-the-setup-project"></a>Para crear el proyecto de instalación  
  
1. En **el Explorador de soluciones**, haga clic en el nodo de solución y, a continuación, haga clic en **Agregar nuevo proyecto**.  
  
2. En el **nuevo proyecto** cuadro de diálogo, expanda **otros tipos de proyectos** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield. Asigne al nuevo proyecto `MySetup` y, a continuación, haga clic en **Aceptar**.  
  
3. Si InstallShield Limited Edition ya está instalado, continúe con el paso siguiente.  
  
    Si ya no está instalado InstallShield Limited Edition, aparece la página de descarga de InstallShield. Siga las instrucciones para descargar e instalar el producto, la elección de la versión de InstallShield que sea compatible con su versión de Visual Studio. Debe decidir si desea registrar la instalación de InstallShield o utilizarlo como una evaluación. Debe reiniciar Visual Studio después de completar la instalación.  
  
   > [!IMPORTANT]
   >  Debe iniciar Visual Studio como administrador antes de crear un proyecto de InstallShield. Si no lo hace, obtendrá un error al compilar el proyecto.  
  
   Los pasos siguientes muestran cómo configurar el proyecto de instalación.  
  
> [!IMPORTANT]
>  Asegúrese de que ha creado la configuración de lanzamiento del proyecto shell aislado de al menos una vez antes de configurar el proyecto de instalación.  
  
#### <a name="to-configure-the-setup-project"></a>Para configurar el proyecto de instalación  
  
1.  En el **el Explorador de soluciones**, en el **MySetup** del proyecto, elija **Project Assistant**. En la fila inferior de la **Project Assistant** ventana, elija **información de la aplicación**. Escriba **Fabrikam** como nombre de su compañía y **Fabrikam música Editor** como el nombre de la aplicación. Elija la flecha de avance en la parte inferior derecha de la **Project Assistant**.  
  
2.  Seleccione **Sí** en **requiere la aplicación cualquier software pueda instalarse en el equipo?** y, a continuación, seleccione **paquete completo de Microsoft .NET Framework 4.5**.  
  
3.  Elija la **archivos de la aplicación** situado en la parte inferior de la ventana y asegúrese de que el **Fabrikam música Editor** se selecciona la carpeta.  
  
4.  Elija la **agregar archivos** botón. En el **agregar archivos** diálogo cuadro, agregue los siguientes archivos desde el **MyVSShellStub\Release** carpeta:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Haga clic en el **agregar resultados del proyecto** botón y agregue **MyVSShellStub principal o de salida**. Haga clic en **Aceptar**.  
  
6.  En el panel izquierdo, bajo **equipo de destino**, haga clic en el **Fabrikam música Editor [INSTALLDIR]** nodo y agregue un **nueva carpeta** denominado **extensiones** .  
  
7.  Haga clic en el **extensiones** nodo en el panel izquierdo y agregue una nueva carpeta denominada **aplicación**.  
  
8.  Seleccione el **aplicación** carpeta y haga clic en el **agregar resultados del proyecto** , a continuación, seleccione el resultado principal del proyecto MyVSShellStub.AboutBoxPackage.  
  
9. Haga clic en el **agregar archivos** botón y desde la carpeta \MyVSShellStub\Release\Extensions\Application\, agregue los siguientes archivos:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Haga clic en el **Fabrikam música Editor [INSTALLDIR]** nodo en el panel izquierdo y agregue una nueva carpeta denominada **1033**.  
  
11. Seleccione la carpeta 1033 y, a continuación, haga clic en el **agregar resultados del proyecto** botón y seleccione el resultado principal del proyecto MyVSShellStubUI.  
  
12. Mover a la **accesos directos a aplicaciones** ventana.  
  
13. Haga clic en **New** para crear un acceso directo y seleccione **\Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output [ProgramFilesFolder]**.  
  
14. Mover a la **entrevista de la instalación** panel.  
  
15. Establece todos los elementos en **No**.  
  
16. En **el Explorador de soluciones**, en el proyecto MySetup, abra **definir requisitos de configuración y las acciones \ requisitos**. El **requisitos** abre la ventana.  
  
17. Haga clic en **requisitos de Software del sistema** y seleccione **crear nueva condición iniciar**. El **Asistente para la búsqueda del sistema** aparece.  
  
18. En el **lo que desea buscar?** panel, elija **entrada del registro** en la lista desplegable y haga clic en **siguiente**.  
  
19. En el **cómo desea buscar?** panel, seleccione **HKEY_LOCAL_MACHINE** como la raíz del registro. Escriba **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 64 bits o **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 32 bits y escriba  **Instalar** como el valor del registro. Haga clic en **Siguiente**.  
  
20. En el **¿qué desea hacer con el valor?** panel, escriba **este producto requiere Visual Studio 2015 aislado Shell Redistributable instalarse.** como el texto para mostrar y haga clic en **finalizar**.  
  
21. Recompile la solución de shell aislado para crear el proyecto de instalación.  
  
     Puede encontrar el archivo setup.exe en la carpeta siguiente:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Probar el programa de instalación  
 Para probar el programa de instalación, copie el archivo setup.exe en un equipo diferente y ejecute el ejecutable del programa de instalación. Debe ser capaz de ejecutar la aplicación de shell aislado.

