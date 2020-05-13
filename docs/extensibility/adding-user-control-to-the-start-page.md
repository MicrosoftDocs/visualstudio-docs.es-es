---
title: Adición de control de usuario a la página de inicio de la página de inicio de la página de inicio de la página de inicio Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740130"
---
# <a name="add-user-control-to-the-start-page"></a>Agregar control de usuario a la página de inicio

En este tutorial se muestra cómo agregar una referencia DLL a una página de inicio personalizada. En el ejemplo se agrega un control de usuario a la solución, se compila el control de usuario y, a continuación, se hace referencia al ensamblado compilado desde el archivo *.xaml* de la página de inicio. Una nueva pestaña hospeda el control de usuario, que funciona como un explorador web básico.

Puede usar el mismo proceso para agregar cualquier ensamblado al que se pueda llamar desde un archivo *.xaml.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Agregar un control de usuario WPF wpf a la solución

En primer lugar, agregue un control de usuario de Windows Presentation Foundation (WPF) a la solución de página de inicio.

1. Cree una página de inicio mediante la creación en [Crear una página](../extensibility/creating-a-custom-start-page.md)de inicio personalizada .

2. En el **Explorador**de soluciones , haga clic con el botón secundario en la solución, haga clic en **Agregar**y, a continuación, haga clic en **Nuevo proyecto**.

3. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto** , expanda el nodo **Visual Basic** o **Visual C.** y haga clic en **Windows**. En el panel central, seleccione Biblioteca de controles de usuario de **WPF**.

4. Asigne un `WebUserControl` nombre al control y, a continuación, haga clic en **Aceptar**.

## <a name="implement-the-user-control"></a>Implementar el control de usuario

Para implementar un control de usuario de WPFWPF, compile la interfaz de usuario (UI) en XAML y, a continuación, escriba los eventos de código subyacente en C- u otro lenguaje .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Para escribir el XAML para el control de usuario

1. Abra el archivo XAML para el control de usuario. En `<Grid>` el elemento, agregue las siguientes definiciones de fila al control.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. En el `<Grid>` elemento principal, `<Grid>` agregue el siguiente elemento nuevo, que contiene un cuadro de texto para escribir direcciones Web y un botón para establecer la nueva dirección.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Agregue el siguiente marco al `<Grid>` elemento de `<Grid>` nivel superior justo después del elemento que contiene el botón y el cuadro de texto.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. En el ejemplo siguiente se muestra el XAML completado para el control de usuario.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Para escribir los eventos de código subyacente para el control de usuario

1. En el diseñador XAML, haz doble clic en el botón **Establecer dirección** que agregaste al control.

    El archivo *UserControl1.cs* se abre en el editor de código.

2. Rellene el controlador de eventos SetButton_Click de la siguiente manera.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Este código establece la dirección Web que se escribe en el cuadro de texto como destino para el explorador web. Si la dirección no es válida, el código produce un error.

3. También debe controlar el evento WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Compile la solución.

## <a name="add-the-user-control-to-the-start-page"></a>Agregue el control de usuario a la página de inicio

Para que este control esté disponible para el proyecto de página de inicio, en el archivo de proyecto de página de inicio, agregue una referencia a la nueva biblioteca de controles. A continuación, puede agregar el control al marcado XAML de la página de inicio.

1. En el **Explorador**de soluciones , en el proyecto Página de inicio , haga clic con el botón secundario en **Referencias** y, a continuación, haga clic en **Agregar referencia**.

2. En la pestaña **Proyectos** , seleccione **WebUserControl** y, a continuación, haga clic en **Aceptar**.

3. En el menú **Compilar**, haga clic en **Compilar solución**.

    La creación de la solución hace que el control de usuario esté disponible para IntelliSense para otros archivos de la solución.

    Para agregar el control al marcado XAML de la página de inicio, agregue una referencia de espacio de nombres al ensamblado y, a continuación, coloque el control en la página.

### <a name="to-add-the-control-to-the-markup"></a>Para agregar el control al marcado

1. En el Explorador de **soluciones**, abra el archivo *.xaml* de la página de inicio.

2. En el panel **XAML,** agregue la siguiente <xref:System.Windows.Controls.Grid> declaración de espacio de nombres al elemento de nivel superior.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. En el panel **XAML,** desplázate hasta la \<sección Cuadrícula>.

    La sección <xref:System.Windows.Controls.TabControl> contiene un <xref:System.Windows.Controls.Grid> elemento de un elemento.

4. Agregue \<un TabControl> \<elemento que contiene un TabItem> que contiene una referencia al control de usuario.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Ahora puede probar el control.

## <a name="test-a-manually-created-custom-start-page"></a>Pruebe una página de inicio personalizada creada manualmente

1. Copie el archivo XAML y los archivos de texto o archivos de marcado compatibles en la carpeta *%USERPROFILE%-Mis documentos-Visual Studio 2015-StartPages.\\ *

2. Si la página de inicio hace referencia a los controles o tipos de ensamblados que Visual Studio no instala, copie los ensamblados y péguelos en la carpeta de instalación de _Visual Studio_**.\\**

3. En un símbolo del sistema de Visual Studio, escriba **devenv /rootsuffix Exp** para abrir una instancia experimental de Visual Studio.

4. En la instancia experimental, vaya a**Environment** >  **la** > página**Inicio** del entorno de**opciones** > de herramientas y seleccione el archivo XAML en el menú desplegable Personalizar página de **inicio.**

5. En el menú **Vista** , haga clic en **Página de inicio**.

    Se debe mostrar la página de inicio personalizada. Si desea cambiar cualquier archivo, debe cerrar la instancia experimental, realizar los cambios, copiar y pegar los archivos modificados y, a continuación, volver a abrir la instancia experimental para ver los cambios.

## <a name="see-also"></a>Vea también

- [Controles de contenedor WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Tutorial: Agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
