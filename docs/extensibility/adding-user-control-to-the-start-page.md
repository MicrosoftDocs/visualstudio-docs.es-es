---
title: Agregar el control de usuario a la página de inicio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 8000c6cc067f61a64c71b8c8ac4f5c0176504cd4
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903387"
---
# <a name="add-user-control-to-the-start-page"></a>Agregar control de usuario a la página de inicio

En este tutorial se muestra cómo agregar una referencia de DLL a una página de inicio personalizada. En el ejemplo se agrega un control de usuario a la solución, se compila el control de usuario y, a continuación, se hace referencia al ensamblado compilado desde el archivo *. Xaml* de la Página principal. Una nueva pestaña hospeda el control de usuario, que funciona como un explorador web básico.

Puede usar el mismo proceso para agregar cualquier ensamblado al que se pueda llamar desde un archivo *. Xaml* .

## <a name="add-a-wpf-user-control-to-the-solution"></a>Agregar un control de usuario de WPF a la solución

En primer lugar, agregue un control de usuario de Windows Presentation Foundation (WPF) a la solución de página de inicio.

1. Cree una página de inicio mediante creado en [crear una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md).

2. En **Explorador de soluciones**, haga clic con el botón secundario en la solución, haga clic en **Agregar**y, a continuación, haga clic en **nuevo proyecto**.

3. En el panel izquierdo del cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual Basic** o **Visual C#** y haga clic en **Windows**. En el panel central, seleccione **biblioteca de controles de usuario de WPF**.

4. Asigne un nombre al control `WebUserControl` y haga clic en **Aceptar**.

## <a name="implement-the-user-control"></a>Implementar el control de usuario

Para implementar un control de usuario de WPF, compile la interfaz de usuario (UI) en XAML y, a continuación, escriba los eventos de código subyacente en C# u otro lenguaje .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Para escribir el código XAML para el control de usuario

1. Abra el archivo XAML para el control de usuario. En el `<Grid>` elemento, agregue las siguientes definiciones de fila al control.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. En el `<Grid>` elemento principal, agregue el siguiente `<Grid>` elemento nuevo, que contiene un cuadro de texto para escribir las direcciones web y un botón para establecer la nueva dirección.

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

3. Agregue el marco siguiente al elemento de nivel superior `<Grid>` justo después del `<Grid>` elemento que contiene el botón y el cuadro de texto.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. En el ejemplo siguiente se muestra el código XAML completado para el control de usuario.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Para escribir los eventos de código subyacente del control de usuario

1. En el diseñador XAML, haga doble clic en el botón **establecer dirección** que ha agregado al control.

    El archivo *UserControl1.CS* se abre en el editor de código.

2. Rellene el controlador de eventos SetButton_Click como se indica a continuación.

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

    Este código establece la dirección web que se escribe en el cuadro de texto como destino del explorador Web. Si la dirección no es válida, el código produce un error.

3. También debe controlar el evento WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Compile la solución.

## <a name="add-the-user-control-to-the-start-page"></a>Agregar el control de usuario a la página de inicio

Para que este control esté disponible para el proyecto de la página de inicio, en el archivo de proyecto de la página de inicio, agregue una referencia a la nueva biblioteca de controles. Después, puede Agregar el control al marcado XAML de la página de inicio.

1. En **Explorador de soluciones**, en el proyecto de la página de inicio, haga clic con el botón secundario en **referencias** y luego haga clic en **Agregar referencia**.

2. En la pestaña **proyectos** , seleccione **WebUserControl** y, a continuación, haga clic en **Aceptar**.

3. En el menú **Compilar** , haga clic en **Compilar solución**.

    Al compilar la solución, el control de usuario estará disponible para IntelliSense para otros archivos de la solución.

    Para agregar el control al marcado XAML de la página de inicio, agregue una referencia de espacio de nombres al ensamblado y, a continuación, coloque el control en la página.

### <a name="to-add-the-control-to-the-markup"></a>Para agregar el control al marcado

1. En **Explorador de soluciones**, abra el archivo *. Xaml* de la Página principal.

2. En el panel **XAML** , agregue la siguiente declaración de espacio de nombres al elemento de nivel superior <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. En el panel **XAML** , desplácese hasta la \<Grid> sección.

    La sección contiene un <xref:System.Windows.Controls.TabControl> elemento en un <xref:System.Windows.Controls.Grid> elemento.

4. Agregue un \<TabControl> elemento que contenga una \<TabItem> referencia al control de usuario.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Ahora puede probar el control.

## <a name="test-a-manually-created-custom-start-page"></a>Probar una página de inicio personalizada creada manualmente

1. Copie el archivo XAML, y los archivos de texto o de marcado auxiliares, en la carpeta *%userprofile%\My Documentos\visual Studio 2015 \\ \ StartPages* .

2. Si la página de inicio hace referencia a los controles o tipos de los ensamblados que no se instalan con Visual Studio, copie los ensamblados y péguelos en la _carpeta de instalación de Visual Studio_** \\ \Common7\IDE\PrivateAssemblies**.

3. En un símbolo del sistema de Visual Studio, escriba **devenv/Rootsuffix exp** para abrir una instancia experimental de Visual Studio.

4. En la instancia experimental, vaya a la **Tools**  >  Página de inicio del entorno**Opciones**de herramientas  >  **Environment**  >  **Startup** y seleccione el archivo XAML en el menú desplegable **Personalizar Página principal** .

5. En el menú **Vista** , haga clic en **Página de inicio**.

    Se debe mostrar la página de inicio personalizada. Si desea cambiar cualquier archivo, debe cerrar la instancia experimental, realizar los cambios, copiar y pegar los archivos modificados y, a continuación, volver a abrir la instancia experimental para ver los cambios.

## <a name="see-also"></a>Vea también

- [Controles de contenedor de WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Tutorial: agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
