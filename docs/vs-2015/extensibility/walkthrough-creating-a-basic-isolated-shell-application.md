---
title: 'Tutorial: crear una aplicación de Shell aislado básica | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6192eb5583e7d0bc37518e995aacccad643cc9ec
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850347"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Tutorial: crear una aplicación básica de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo crear una solución de Shell aislado, personalizar la ventana de herramientas de ayuda y crear un programa de instalación que instale el shell aislado.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md). Para implementar el shell aislado, también debe usar el paquete redistribuible de Visual Studio Shell (aislado).  
  
## <a name="creating-an-isolated-shell-solution"></a>Crear una solución de Shell aislado  
 En esta sección se muestra cómo usar la plantilla de proyecto aislado de Visual Studio Shell para crear una solución de Shell aislado. La solución contiene los siguientes proyectos:  
  
- *Nombredesolución*. Proyecto AboutBoxPackage, que le permite personalizar la apariencia del cuadro de ayuda/acerca de.  
  
- El proyecto ShellExtensionsVSIX, que contiene el archivo source. Extension. vsixmanifest que define los distintos componentes de la aplicación de Shell aislado.  
  
- El proyecto *solutionname* , que genera el archivo ejecutable que invoca la aplicación de Shell aislado. Este proyecto contiene la carpeta de personalización de Shell, que le permite personalizar la apariencia y el comportamiento de la aplicación de Shell aislado.  
  
- El proyecto de interfaz de usuario de *solutionname* , que genera un ensamblado satélite que define los comandos de menú activos y las cadenas localizables.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Para crear una solución básica de Shell aislado  
  
1. Abra Visual Studio y cree un nuevo proyecto.  
  
2. En la ventana **nuevo proyecto** , expanda **otros tipos de proyecto** y, a continuación, **extensibilidad**. Seleccione la plantilla de proyecto **aislado de Visual Studio Shell** .  
  
3. Asigne al proyecto el nombre `MyVSShellStub` y especifique una ubicación. Asegúrese de que la opción **Crear directorio para la solución** está activada y, a continuación, haga clic en **Aceptar**.  
  
     La nueva solución aparece en **Explorador de soluciones**.  
  
4. Compile la solución e inicie la depuración de la aplicación de Shell aislado.  
  
     Aparece el shell aislado de Visual Studio. La barra de título lee **MyVSShellStub**. El icono de la barra de título se genera a partir de \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personalización del nombre y el icono de la aplicación  
 Es posible que desee personalizar la aplicación con el nombre de su empresa y su logotipo en la barra de título. En los pasos siguientes se muestra cómo cambiar el nombre y el icono que se muestran en la barra de título de la aplicación personalizada cambiando el archivo de definición del paquete, MyVSShellStub. Application. pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Para personalizar el nombre y el icono de la aplicación  
  
1. En el proyecto MyVSShellStub, abra \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2. Cambie el valor del elemento `AppName` a **"appname" = "fabrikam Music Editor"**  
  
3. Para cambiar el icono de la aplicación, copie un icono diferente en el directorio \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Cambie el nombre del archivo ApplicationIcon. ico existente a ApplicationIcon1. ico. Cambie el nombre del nuevo archivo a ApplicationIcon. ico.  
  
4. Compile la solución y comience la depuración. Aparece el IDE de Shell aislado. La barra de título tiene el icono nuevo junto a las palabras **Editor de música Fabrikam**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personalización de la Página principal del explorador Web predeterminado  
 En esta sección se muestra cómo cambiar la Página principal predeterminada de la ventana del **explorador Web** cambiando el archivo de definición del paquete.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Para personalizar la Página principal del explorador Web predeterminado  
  
1. En el archivo MyVSShellStub. Application. pkgdef, cambie el valor del elemento `DefaultHomePage` a "<https://www.microsoft.com>".  
  
2. Vuelva a generar el proyecto MyVSShellStub.  
  
3. Compile la solución y comience la depuración.  
  
4. En **Ver/otras ventanas**, haga clic en **explorador Web**. La ventana del **explorador Web** muestra la Página principal de Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Quitar el comando de impresión  
 El archivo. Vsct de un proyecto de interfaz de usuario de Shell aislado se compone de un conjunto de declaraciones con el formato `<Define name=No_`*elemento*`>`, donde *elemento* es uno de los menús y comandos de Visual Studio estándar.  
  
 Si se quita el comentario de una declaración, ese menú o comando se excluye del shell aislado. Por el contrario, si una declaración está comentada, el menú o el comando se incluyen en el shell aislado.  
  
 En los pasos siguientes, quitará el comentario del comando Print en el archivo. Vsct.  
  
#### <a name="to-remove-the-print-command"></a>Para quitar el comando imprimir  
  
1. Compruebe que el comando **Imprimir** aparece en el menú **archivo** de la aplicación de Shell aislado.  
  
2. En el proyecto MyVSShellStubUI, abra \Resource Files\MyVSShellStubUI.vsct para editarlo.  
  
3. Quite la marca de comentario de esta línea:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Esto quita el comando imprimir.  
  
5. Iniciar la depuración de la aplicación de Shell aislado. Compruebe que el comando **archivo/imprimir** ha desaparecido.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Quitar características del shell aislado  
 Puede quitar algunos de los paquetes que se cargan con Visual Studio editando el archivo. pkgundef si no desea esas características en la aplicación de Shell aislado personalizada. El paquete se especifica en una de las subclaves de la clave del registro $RootKey $ \Packages.  
  
> [!NOTE]
> Para encontrar los GUID de características de Visual Studio, vea [GUID de paquete de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 En el siguiente procedimiento se muestra cómo quitar el editor XML del shell aislado.  
  
#### <a name="to-remove-the-xml-editor"></a>Para quitar el editor XML  
  
1. Abra el archivo MyVSShellStub. pkgundef en la carpeta de personalización de Shell del proyecto MyVSShellStub.  
  
2. Quite la marca de comentario de la línea siguiente:  
  
     [$RootKey$\Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. Recompile la solución e inicie la depuración del shell aislado. Abra un archivo XML, por ejemplo, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Compruebe que las palabras clave XML del archivo no están coloreadas y que al escribir "<" en una línea no se muestra la información sobre herramientas XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personalización del cuadro de ayuda/acerca de  
 Puede personalizar el cuadro ayuda/acerca de, que se crea como parte de la plantilla de proyecto de Shell aislado.  
  
#### <a name="to-customize-the-company-name"></a>Para personalizar el nombre de la empresa  
  
1. El nombre de la empresa, la información de copyright, la versión del producto y la descripción del producto se encuentran en el proyecto MyVSShellStub. AboutBoxPackage, en el archivo \Properties\AssemblyInfo.cs. Abra este archivo.  
  
2. Cambie el valor de `AssemblyCompany` a **Fabrikam**, los valores de `AssemblyProduct` y `AssemblyTitle` a **Fabrikam Music Editor**y el valor de `AssemblyCopyright` a **Copyright © Fabrikam 2015**:  
  
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
  
3. Para agregar una descripción del producto, cambie el valor de `AssemblyDescription` a **la descripción de Fabrikam Music Editor.** :  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Inicie la depuración y, en la aplicación de Shell aislado, abra el cuadro de **ayuda/acerca** de. Debería ver las cadenas modificadas. El título del cuadro de ayuda/acerca de es el mismo que el valor de `AssemblyTitle` de AssemblyInfo.cs.  
  
5. Las propiedades del propio cuadro **ayuda/acerca** de se encuentran en el archivo MyVSShellStub. AboutBoxPackage\AboutBox.Xaml. Para cambiar el ancho del cuadro de ayuda/acerca de, vaya al bloque `AboutDialogStyle` y establezca la propiedad `Width` en 200:  
  
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
  
6. Recompile la solución e inicie la depuración del shell aislado. El cuadro ayuda/acerca de debe ser aproximadamente cuadrado.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Antes de implementar la aplicación de Shell aislado  
 La aplicación de Shell aislado se puede instalar en cualquier equipo que tenga el paquete redistribuible de Visual Studio Shell (aislado). Para obtener más información sobre el paquete redistribuible, vea el sitio web de [descargas de extensibilidad de Visual Studio](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="deploying-the-isolated-shell-application"></a>Implementar la aplicación de Shell aislado  
 La aplicación de Shell aislado se implementa en un equipo de destino mediante la creación de un proyecto de instalación. Debe especificar estos elementos:  
  
- El diseño de las carpetas y archivos en el equipo de destino.  
  
- Las condiciones de inicio que garantizan que los .NET Framework y el tiempo de ejecución de Visual Studio Shell están instalados en el equipo de destino.  
  
  En el procedimiento siguiente, deberá instalar InstallShield Limited Edition en el equipo.  
  
#### <a name="to-create-the-setup-project"></a>Para crear el proyecto de instalación  
  
1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución y, a continuación, haga clic en **Agregar nuevo proyecto**.  
  
2. En el cuadro de diálogo **nuevo proyecto** , expanda **otros tipos de proyectos** y, después, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield. Asigne al nuevo proyecto el nombre `MySetup` y, a continuación, haga clic en **Aceptar**.  
  
3. Si InstallShield Limited Edition ya está instalado, continúe con el paso siguiente.  
  
    Si InstallShield Limited Edition no está ya instalado, aparece la página de descarga de InstallShield. Siga las instrucciones para descargar e instalar el producto y elija la versión de InstallShield que sea compatible con su versión de Visual Studio. Debe decidir si desea registrar la instalación de InstallShield o utilizarla como evaluación. Debe reiniciar Visual Studio después de completar la instalación.  
  
   > [!IMPORTANT]
   > Debe iniciar Visual Studio como administrador antes de crear un proyecto de InstallShield. Si no lo hace, recibirá un error al compilar el proyecto.  
  
   En los pasos siguientes se muestra cómo configurar el proyecto de instalación.  
  
> [!IMPORTANT]
> Asegúrese de haber compilado la configuración de lanzamiento del proyecto de Shell aislado al menos una vez antes de configurar el proyecto de instalación.  
  
#### <a name="to-configure-the-setup-project"></a>Para configurar el proyecto de instalación  
  
1. En el **Explorador de soluciones**, en el proyecto de mi **instalación** , elija **Asistente para proyectos**. En la fila inferior de la ventana del **Asistente de proyectos** , elija información de la **aplicación**. Escriba **Fabrikam** como nombre de la compañía y **Editor de música de Fabrikam** como nombre de la aplicación. Elija la flecha hacia delante que se encuentra en la parte inferior derecha del **Asistente para proyectos**.  
  
2. Seleccione **sí** en **¿su aplicación requiere que se instale software en el equipo?** y, a continuación, seleccione **paquete completo de Microsoft .NET Framework 4,5**.  
  
3. Elija el botón **archivos de aplicación** situado en la parte inferior de la ventana y asegúrese de que la carpeta **Fabrikam Music Editor** está seleccionada.  
  
4. Elija el botón **Agregar archivos** . En el cuadro de diálogo **Agregar archivos** , agregue los siguientes archivos de la carpeta **MyVSShellStub\Release** :  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll.manifest  
  
    4. MyVSShellStub.pkgdef  
  
    5. MyVSShellStub.pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. Splash. bmp  
  
5. Haga clic en el botón **Agregar resultados del proyecto** y agregue **MyVSShellStub/Primary Output**. Haga clic en **Aceptar**.  
  
6. En el panel izquierdo, en **equipo de destino**, haga clic con el botón secundario en el nodo **Fabrikam Music Editor [INSTALLDIR]** y agregue una **nueva carpeta** denominada **extensiones**.  
  
7. Haga clic con el botón secundario en el nodo **extensiones** en el panel izquierdo y agregue una nueva carpeta denominada **aplicación**.  
  
8. Seleccione la carpeta de la **aplicación** y haga clic en el botón **Agregar resultados del proyecto** y, a continuación, seleccione la salida principal del proyecto MyVSShellStub. AboutBoxPackage.  
  
9. Haga clic en el botón **Agregar archivos** y, en la carpeta \MyVSShellStub\Release\Extensions\Application\, agregue los siguientes archivos:  
  
    - MyVSShellStub.AboutBoxPackage.pkgdef  
  
    - MyVSShellStub.Application.pkgdef  
  
10. Haga clic con el botón secundario en el nodo **Fabrikam Music Editor [INSTALLDIR]** en el panel izquierdo y agregue una nueva carpeta denominada **1033**.  
  
11. Seleccione la carpeta 1033 y, a continuación, haga clic en el botón **Agregar resultados del proyecto** y seleccione la salida principal del proyecto MyVSShellStubUI.  
  
12. Desplácese a la ventana **accesos directos** de la aplicación.  
  
13. Haga clic en **nuevo** para crear un acceso directo y seleccionar **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Vaya al panel de la **entrevista de instalación** .  
  
15. Establecer todos los elementos en **no**.  
  
16. En **Explorador de soluciones**, en el proyecto de mi instalación, Abra **definir requisitos y acciones de instalación \ requisitos**. Se abre la ventana **requisitos** .  
  
17. Haga clic con el botón derecho en **requisitos de software del sistema** y seleccione **crear nueva condición de inicio**. Aparece el **Asistente para búsqueda del sistema** .  
  
18. En el panel **¿qué desea buscar?** , elija **entrada del registro** en la lista desplegable y haga clic en **siguiente**.  
  
19. En el panel **¿Cómo desea buscarlo?** , seleccione **HKEY_LOCAL_MACHINE** como la raíz del registro. Escriba **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 64 bits o **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 32 bits y escriba **install** como valor del registro. Haga clic en **Siguiente**.  
  
20. En el panel **¿qué desea hacer con el valor?** , escriba **este producto requiere que se instale el paquete redistribuible de Shell aislado de Visual Studio 2015.** como texto para mostrar y haga clic en **Finalizar**.  
  
21. Vuelva a generar la solución de Shell aislado para crear el proyecto de instalación.  
  
     Puede encontrar el archivo Setup. exe en la siguiente carpeta:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Probar el programa de instalación  
 Para probar la instalación, copie el archivo Setup. exe en otro equipo y ejecute el ejecutable de instalación. Debe poder ejecutar la aplicación de Shell aislado.
