---
title: 'Tutorial: Creación de un SDK con C o Visual Basic. Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697552"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Tutorial: Crear un SDK con C o Visual Basic
En este tutorial, aprenderá a crear un SDK de biblioteca de matemáticas simple mediante Visual C- y, a continuación, empaquetar el SDK como una extensión de Visual Studio (VSIX). Completará los siguientes procedimientos:

- [Para crear el componente SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Para crear el proyecto de extensión SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Para crear una aplicación de ejemplo que use la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Para crear el componente SimpleMath Windows Runtime

1. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

2. En la lista de plantillas, expanda **Visual C** o **Visual Basic**, elija el nodo **Tienda Windows** y, a continuación, elija la plantilla Componente de Windows en tiempo de **ejecución.**

3. En el cuadro **Nombre,** especifique **SimpleMath**y, a continuación, elija el botón **Aceptar.**

4. En el **Explorador**de soluciones , abra el menú contextual del nodo de proyecto **SimpleMath** y, a continuación, elija **Propiedades**.

5. Cambie el nombre **de Class1.cs** para **Arithmetic.cs** y actualícelo para que coincida con el código siguiente:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. En el **Explorador**de soluciones , abra el menú contextual del nodo **Solución 'SimpleMath'** y, a continuación, elija **Configuration Manager**.

    Se abre el cuadro de diálogo Administrador de **configuración.**

7. En la lista Configuración de **la solución activa,** elija **Liberar**.

8. En la columna **Configuration (Configuración),** compruebe que la fila **SimpleMath** está establecida en **Release (Liberar)** y, a continuación, elija el botón **Close (Cerrar)** para aceptar el cambio.

   > [!IMPORTANT]
   > El SDK del componente SimpleMath solo incluye una configuración. Esta configuración debe ser la compilación de la versión o [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]las aplicaciones que usan el componente no pasarán la certificación para el archivo .

9. En el **Explorador**de soluciones , abra el menú contextual del nodo de proyecto **SimpleMath** y, a continuación, elija **Compilar**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Para crear el proyecto de extensión SimpleMathVSIX

1. En el menú contextual del nodo **Solución 'SimpleMath',** elija **Agregar** > **nuevo proyecto**.

2. En la lista de plantillas, expanda **Visual C** o **Visual Basic**, elija el nodo **Extensibilidad** y, a continuación, elija la plantilla **Proyecto VSIX.**

3. En el cuadro **Nombre,** especifique **SimpleMathVSIX**y, a continuación, elija el botón **Aceptar.**

4. En **el Explorador**de soluciones , elija el elemento **source.extension.vsixmanifest.**

5. En la barra de menús, elija **Ver** > **código**.

6. Reemplace el XML existente por el siguiente XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. En **el Explorador**de soluciones , elija el proyecto **SimpleMathVSIX.**

8. En la barra de menús, elija **Proyecto** > **agregar nuevo elemento**.

9. En la lista **Deelementos comunes**, expanda **Datos**y, a continuación, elija **Archivo XML**.

10. En el cuadro `SDKManifest.xml` **Nombre,** especifique y, a continuación, elija el botón **Agregar.**

11. En el **Explorador**de soluciones `SDKManifest.xml`, abra el menú contextual para , elija **Propiedades**y, a continuación, cambie el valor de la propiedad **Incluir en VSIX** a **True**.

12. Sustituye el contenido del archivo por el siguiente código XML:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. En el **Explorador**de soluciones , abra el menú contextual del proyecto **SimpleMathVSIX,** elija **Agregar**y, a continuación, elija **Nueva carpeta**.

14. Cambie el `references`nombre de la carpeta a .

15. Abra el menú contextual de la carpeta **Referencias,** elija **Agregar**y, a continuación, elija **Nueva carpeta**.

16. Cambie el `commonconfiguration`nombre de la subcarpeta a , `neutral`cree una subcarpeta dentro de ella y asigne un nombre a la subcarpeta .

17. Repita los cuatro pasos anteriores, esta `redist`vez cambiando el nombre de la primera carpeta a .

     El proyecto ahora contiene la siguiente estructura de carpetas:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. En el **Explorador**de soluciones , abra el menú contextual del proyecto **SimpleMath** y, a continuación, elija **Abrir carpeta en el Explorador**de archivos .

19. En **el Explorador**de archivos , desplácese hasta la carpeta *bin-Release,* abra el menú contextual del archivo **SimpleMath.winmd** y, a continuación, elija **Copy**.

20. En el **Explorador**de soluciones , pegue el archivo en la carpeta *references-commonconfiguration-neutral* del proyecto **SimpleMathVSIX.**

21. Repita el paso anterior, pegando el archivo **SimpleMath.pri** en la carpeta *redist-commonconfiguration-neutral* en el proyecto **SimpleMathVSIX.**

22. En **el Explorador**de soluciones , elija **SimpleMath.winmd**.

23. En la barra de menús, elija**Propiedades** de **vista** > (Teclado: elija la tecla **F4).**

24. En la ventana **Propiedades** , cambie la propiedad Acción de **compilación** a **Contenido**y, a continuación, cambie la propiedad **Incluir en VSIX** a **True**.

25. En **el Explorador**de soluciones , repita este proceso para **SimpleMath.pri**.

26. En **el Explorador**de soluciones , elija el proyecto **SimpleMathVSIX.**

27. En la barra de menús, elija **Build** > **Build SimpleMathVSIX**.

28. En el **Explorador**de soluciones , abra el menú contextual del proyecto **SimpleMathVSIX** y, a continuación, elija **Abrir carpeta en el Explorador**de archivos .

29. En **el Explorador**de archivos , desplácese hasta la carpeta *.bin-Release* y, a continuación, ejecute *SimpleMathVSIX.vsix* para instalarlo.

30. Elija el botón **Instalar,** espere a que finalice la instalación y, a continuación, reinicie Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Para crear una aplicación de ejemplo que use la biblioteca de clases

1. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

2. En la lista de plantillas, expanda **Visual C** o **Visual Basic**y, a continuación, elija el nodo Tienda **Windows** .

3. Elija la plantilla **Aplicación en blanco,** asigne al proyecto el nombre **ArithmeticUI**y, a continuación, elija el botón **Aceptar.**

4. En el **Explorador**de soluciones , abra el menú contextual del proyecto **ArithmeticUI** y, a continuación, elija **Agregar** > **referencia**.

5. En la lista de tipos de referencia, expanda **Windows**y, a continuación, elija **Extensiones**.

6. En el panel de detalles, elija la extensión **WinRT Math Library.**

    Aparece información adicional sobre el SDK. Puede elegir el vínculo Más https://msdn.microsoft.com/ **información** para abrir , como especificó en el archivo SDKManifest.xml anteriormente en este tutorial.

7. En el cuadro de diálogo Administrador de **referencias,** active la casilla Biblioteca de **matemáticas de WinRT** y, a continuación, elija el botón **Aceptar.**

8. En la barra de menús, elija **Ver** > **Navegador de objetos**.

9. En la lista **Examinar,** elija **Simple Math**.

     Ahora puede explorar lo que hay en el SDK.

10. En **el Explorador**de soluciones , abra **MainPage.xaml**y reemplace su contenido por el siguiente XAML:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Actualice **MainPage.xaml.cs** para que coincida con el código siguiente:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Elija la tecla **F5** para ejecutar la aplicación.

13. En la aplicación, escriba los dos números, **=** elija una operación y, a continuación, elija el botón.

     Aparece el resultado correcto.

    Ha creado y utilizado correctamente un SDK de extensión.

## <a name="see-also"></a>Vea también
- [Tutorial: Crear un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Tutorial: Crear un SDK con JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
