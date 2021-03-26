---
title: 'Tutorial: crear un SDK con C# o Visual Basic | Microsoft Docs'
description: Aprenda a crear un sencillo SDK de biblioteca matemática mediante Visual C# y, a continuación, empaquete el SDK como una extensión de Visual Studio mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 6ce834a2c949c55a6deeb6b7c7d0a9751771e316
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080403"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Tutorial: crear un SDK mediante C# o Visual Basic
En este tutorial, aprenderá a crear un sencillo SDK de biblioteca matemática usando Visual C# y, a continuación, empaquetará el SDK como extensión de Visual Studio (VSIX). Completará los siguientes procedimientos:

- [Para crear el componente Windows Runtime de SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Para crear el proyecto de extensión SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Para crear una aplicación de ejemplo que usa la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Para crear el componente Windows Runtime de SimpleMath

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de plantillas, expanda **Visual C#** o **Visual Basic**, elija el nodo de la **tienda Windows** y, a continuación, elija la plantilla **componente de Windows Runtime** .

3. En el cuadro **nombre** , especifique **SimpleMath** y elija el botón **Aceptar** .

4. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **SimpleMath** y, a continuación, elija **propiedades**.

5. Cambie el nombre de **Class1. CS** a **aritmético. CS** y actualícelo para que coincida con el código siguiente:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. En **Explorador de soluciones**, abra el menú contextual del nodo **' SimpleMath '** de la solución y, a continuación, elija **Configuration Manager**.

    Se abrirá el cuadro de diálogo **Configuration Manager** .

7. En la lista **configuración de soluciones activas** , elija **versión**.

8. En la columna **configuración** , compruebe que **SimpleMath** fila está establecida en **liberar** y, a continuación, elija el botón **cerrar** para aceptar el cambio.

   > [!IMPORTANT]
   > El SDK del componente SimpleMath incluye solo una configuración. Esta configuración debe ser la versión de lanzamiento, o las aplicaciones que usan el componente no pasarán la certificación para [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **SimpleMath** y, a continuación, elija **compilar**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Para crear el proyecto de extensión SimpleMathVSIX

1. En el menú contextual del nodo **' SimpleMath '** de la solución, elija **Agregar**  >  **nuevo proyecto**.

2. En la lista de plantillas, expanda **Visual C#** o **Visual Basic**, elija el nodo **extensibilidad** y, a continuación, elija la plantilla de **Proyecto VSIX** .

3. En el cuadro **nombre** , especifique **SimpleMathVSIX** y elija el botón **Aceptar** .

4. En **Explorador de soluciones**, elija el elemento **source. Extension. vsixmanifest** .

5. En la barra de menús, elija **Ver** > **Código**.

6. Reemplace el XML existente por el siguiente código XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. En **Explorador de soluciones**, elija el proyecto **SimpleMathVSIX** .

8. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

9. En la lista de **elementos comunes**, expanda **datos** y, a continuación, elija **archivo XML**.

10. En el cuadro **nombre** , especifique `SDKManifest.xml` y, a continuación, elija el botón **Agregar** .

11. En **Explorador de soluciones**, abra el menú contextual de `SDKManifest.xml` , elija **propiedades** y, a continuación, cambie el valor de la propiedad **incluir en VSIX** a **true**.

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

13. En **Explorador de soluciones**, abra el menú contextual del proyecto **SimpleMathVSIX** , elija **Agregar** y, a continuación, elija **nueva carpeta**.

14. Cambie el nombre de la carpeta a `references` .

15. Abra el menú contextual de la carpeta **referencias** , elija **Agregar** y, a continuación, elija **nueva carpeta**.

16. Cambie el nombre de la subcarpeta a `commonconfiguration` , cree una subcarpeta en ella y asigne un nombre a la subcarpeta `neutral` .

17. Repita los cuatro pasos anteriores, esta vez cambiando el nombre de la primera carpeta a `redist` .

     El proyecto contiene ahora la siguiente estructura de carpetas:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. En **Explorador de soluciones**, abra el menú contextual del proyecto **SimpleMath** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.

19. En **el explorador de archivos**, vaya a la carpeta *bin\Release* , abra el menú contextual del archivo **SimpleMath. winmd** y, a continuación, elija **copiar**.

20. En **Explorador de soluciones**, pegue el archivo en la carpeta *References\commonconfiguration\neutral* del proyecto **SimpleMathVSIX** .

21. Repita el paso anterior, pegando el archivo **SimpleMath. PRI** en la carpeta *Redist\commonconfiguration\neutral* del proyecto **SimpleMathVSIX** .

22. En **Explorador de soluciones**, elija **SimpleMath. winmd**.

23. En la barra de menús, elija **Ver**  >  **propiedades** (teclado: elija la tecla **F4** ).

24. En la ventana **propiedades** , cambie la propiedad **acción de compilación** a **contenido** y, a continuación, cambie la propiedad **incluir en VSIX** a **true**.

25. En **Explorador de soluciones**, repita este proceso para **SimpleMath. PRI**.

26. En **Explorador de soluciones**, elija el proyecto **SimpleMathVSIX** .

27. En la barra de menús, **Elija compilar**  >  **compilación SimpleMathVSIX**.

28. En **Explorador de soluciones**, abra el menú contextual del proyecto **SimpleMathVSIX** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.

29. En el **Explorador de archivos**, vaya a la carpeta *\bin\Release* y, a continuación, ejecute *SimpleMathVSIX. vsix* para instalarlo.

30. Elija el botón **instalar** , espere a que finalice la instalación y, a continuación, reinicie Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Para crear una aplicación de ejemplo que usa la biblioteca de clases

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de plantillas, expanda **Visual C#** o **Visual Basic** y, a continuación, elija el nodo de la **tienda Windows** .

3. Elija la plantilla **aplicación vacía** , asigne al proyecto el nombre **ArithmeticUI** y, a continuación, elija el botón **Aceptar** .

4. En **Explorador de soluciones**, abra el menú contextual del proyecto **ArithmeticUI** y, a continuación, elija **Agregar**  >  **referencia**.

5. En la lista de tipos de referencia, expanda **Windows** y, a continuación, elija **extensiones**.

6. En el panel de detalles, elija la extensión de la **biblioteca matemática de WinRT** .

    Aparece información adicional sobre el SDK. Puede elegir el vínculo **más información** para abrir https://msdn.microsoft.com/ , como especificó en el archivo SDKManifest.xml anteriormente en este tutorial.

7. En el cuadro de diálogo **Administrador de referencias** , active la casilla **biblioteca matemática de WinRT** y, a continuación, elija el botón **Aceptar** .

8. En la barra de menús, elija **Ver**  >  **Examinador de objetos**.

9. En la lista **examinar** , elija **matemáticas simples**.

     Ahora puede explorar lo que hay en el SDK.

10. En **Explorador de soluciones**, Abra **mainpage. Xaml** y reemplace su contenido por el código XAML siguiente:

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

11. Actualice **mainpage. Xaml. CS** para que coincida con el código siguiente:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Elija la tecla **F5** para ejecutar la aplicación.

13. En la aplicación, escriba dos números cualesquiera, elija una operación y, a continuación, elija el **=** botón.

     Aparece el resultado correcto.

    Ha creado y usado correctamente un SDK de extensión.

## <a name="see-also"></a>Consulte también
- [Tutorial: crear un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Tutorial: crear un SDK mediante JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
