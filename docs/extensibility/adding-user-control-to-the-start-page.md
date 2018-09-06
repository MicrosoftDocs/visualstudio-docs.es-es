---
title: Agregar Control de usuario a la página de inicio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bcac83d23bae3d8c269a53a95fedb9507245e9f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775831"
---
# <a name="add-user-control-to-the-start-page"></a>Agregar control de usuario a la página de inicio
Este tutorial muestra cómo agregar una referencia de archivo DLL a una página de inicio personalizada. En el ejemplo se agrega un control de usuario a la solución, crea el control de usuario y, a continuación, hace referencia el ensamblado compilado desde la página de inicio *.xaml* archivo. Una nueva pestaña hospeda el control de usuario, que funciona como un explorador Web básico.  
  
 Puede usar el mismo proceso para agregar cualquier ensamblado al que se puede llamar desde una *.xaml* archivo.  
  
## <a name="add-a-wpf-user-control-to-the-solution"></a>Agregue un control de usuario WPF a la solución  
 En primer lugar, agregue un control de usuario de Windows Presentation Foundation (WPF) a la solución de la página de inicio.  
  
1.  Crear una página de inicio mediante el uso que creamos en [crear una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md).  
  
2.  En **el Explorador de soluciones**, haga clic en la solución, haga clic en **agregar**y, a continuación, haga clic en **nuevo proyecto**.  
  
3.  En el panel izquierdo de la **nuevo proyecto** diálogo cuadro, expanda el **Visual Basic** o **Visual C#** nodo y haga clic en **Windows**. En el panel central, seleccione **biblioteca de controles de usuario de WPF**.  
  
4.  Nombre del control `WebUserControl` y, a continuación, haga clic en **Aceptar**.  
  
## <a name="implement-the-user-control"></a>Implementar el control de usuario  
 Para implementar un control de usuario WPF, compile la interfaz de usuario (UI) en XAML y, a continuación, escribir los eventos de código subyacente en C# u otro lenguaje. NET.  
  
### <a name="to-write-the-xaml-for-the-user-control"></a>Para escribir el XAML para el control de usuario  
  
1.  Abra el archivo XAML para el control de usuario. En el `<Grid>` elemento, agregue las siguientes definiciones de fila al control.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  En la ventana principal `<Grid>` elemento, agregue la siguiente nueva `<Grid>` elemento, que contiene un cuadro de texto para escribir las direcciones Web y un botón para establecer la nueva dirección.  
  
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
  
3.  Agregue el siguiente marco a la observación inicial `<Grid>` elemento justo después del `<Grid>` elemento que contiene el botón y un cuadro de texto.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  El ejemplo siguiente muestra el XAML completa para el control de usuario.  
  
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
  
1.  En el Diseñador XAML, haga doble clic en el **establecer dirección** que agregó al control de botón.  
  
     El *UserControl1.cs* archivo se abre en el editor de código.  
  
2.  Rellene el controlador de eventos SetButton_Click como sigue.  
  
    ```csharp  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
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
  
     Este código establece la dirección Web que se escribe en el cuadro de texto como el destino para el explorador Web. Si la dirección no es válida, el código produce un error.  
  
3.  También debe controlar el evento WebFrame_Navigated:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Compile la solución.  
  
## <a name="add-the-user-control-to-the-start-page"></a>Agregar el control de usuario a la página de inicio  
 Para que este control esté disponible para el proyecto de la página de inicio, en el archivo de proyecto de la página de inicio, agregue una referencia a la nueva biblioteca de control. A continuación, puede agregar el control en el marcado XAML de página de inicio.  
  
1.  En **el Explorador de soluciones**, en el proyecto de la página de inicio, haga clic en **referencias** y, a continuación, haga clic en **Agregar referencia**.  
  
2.  En el **proyectos** ficha, seleccione **WebUserControl** y, a continuación, haga clic en **Aceptar**.  
  
3.  En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     Compilar la solución hace que el control de usuario estén disponibles para IntelliSense para otros archivos de la solución.  
  
 Para agregar el control en el marcado XAML de página de inicio, agregue una referencia de espacio de nombres para el ensamblado, a continuación, colocar el control en la página.  
  
### <a name="to-add-the-control-to-the-markup"></a>Para agregar el control al código de marcado  
  
1.  En **el Explorador de soluciones**, abra la página de inicio *.xaml* archivo.  
  
2.  En el **XAML** panel, agregue la siguiente declaración de espacio de nombres a la observación inicial <xref:System.Windows.Controls.Grid> elemento.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  En el **XAML** panel, desplácese hasta la \<cuadrícula > sección.  
  
     La sección contiene un <xref:System.Windows.Controls.TabControl> elemento en un <xref:System.Windows.Controls.Grid> elemento.  
  
4.  Agregar un \<TabControl > que contiene el elemento un \<TabItem > que contiene una referencia al control de usuario.  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 Ahora puede probar el control.  
  
## <a name="test-a-manually-created-custom-start-page"></a>Probar una página de inicio personalizada creada manualmente  
  
1.  Copie el archivo XAML y los archivos de texto o marcado auxiliares archivos, a la *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  carpeta.  
  
2.  Si hace referencia a la página de inicio de los tipos en ensamblados que no se instalan con Visual Studio o los controles, copie los ensamblados y, a continuación, péguelos en _carpeta de instalación de Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  En un símbolo del sistema de Visual Studio, escriba **devenv /rootsuffix Exp** para abrir una instancia experimental de Visual Studio.  
  
4.  En la instancia experimental, vaya a la **herramientas** > **opciones** > **entorno** > **inicio** página y seleccione el archivo XAML desde el **Personalizar página principal** lista desplegable.  
  
5.  En el menú **Vista** , haga clic en **Página de inicio**.  
  
     Debe mostrarse la página de inicio personalizada. Si desea cambiar todos los archivos, debe cerrar la instancia experimental, realice los cambios, copie y pegue los archivos modificados y, a continuación, vuelva a abrir la instancia experimental para ver los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Controles de contenedor WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [Tutorial: Agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)