---
title: 'Tutorial: guardar la configuración de usuario en una página de inicio | Microsoft Docs'
description: Para obtener información sobre cómo conservar la configuración de usuario de la página de inicio, guarde una configuración en el registro mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2f7dddfca06d7bc475286c73087828305464daa5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217221"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Tutorial: guardar la configuración de usuario en una página de inicio

Puede conservar la configuración de usuario de la página de inicio. Al seguir este tutorial, puede crear un control que guarda un valor en el registro cuando el usuario hace clic en un botón y, a continuación, recupera ese valor cada vez que se carga la página de inicio. Dado que la plantilla de proyecto de página de inicio incluye un control de usuario personalizable y el XAML de la página de inicio predeterminada llama a ese control, no es necesario modificar la propia página de inicio.

El almacén de configuración del que se crea una instancia en este tutorial es una instancia de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfaz, que lee y escribe en la siguiente ubicación del registro cuando se llama: **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName>**

Cuando se ejecuta en la instancia experimental de Visual Studio, la configuración almacena las lecturas y escrituras en **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName> .**

Para obtener más información sobre cómo conservar la configuración, vea [extender la configuración de usuario y las opciones](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).
>
> Puede descargar la plantilla de proyecto de página de inicio mediante el **Administrador de extensiones**.

## <a name="set-up-the-project"></a>Configuración del proyecto

1. Cree un proyecto de página de inicio como se describe en [crear una página de inicio personalizada](creating-a-custom-start-page.md). Asigne al proyecto el nombre **SaveMySettings**.

2. En **Explorador de soluciones**, agregue las siguientes referencias de ensamblado al proyecto StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Abra *DataControl. Xaml*.

4. En el panel XAML, en la definición del elemento de nivel superior <xref:System.Windows.Controls.UserControl> , agregue la siguiente declaración de evento después de las declaraciones de espacio de nombres.

    ```xml
    Loaded="OnLoaded"
    ```

5. En el panel de diseño, haga clic en el área principal del control y, a continuación, presione **Supr**.

     Este paso quita el <xref:System.Windows.Controls.Border> elemento y todo lo que contenga y deja solo el elemento de nivel superior <xref:System.Windows.Controls.Grid> .

6. En el **cuadro de herramientas**, arrastre un <xref:System.Windows.Controls.StackPanel> control a la cuadrícula.

7. Arrastre ahora un <xref:System.Windows.Controls.TextBlock> , un <xref:System.Windows.Controls.TextBox> y un botón a <xref:System.Windows.Controls.StackPanel> .

8. Agregue un atributo **x:Name** para <xref:System.Windows.Controls.TextBox> y un `Click` evento para <xref:System.Windows.Controls.Button> , tal y como se muestra en el ejemplo siguiente.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementar el control de usuario

1. En el panel XAML, haga clic con el botón secundario en el `Click` atributo del <xref:System.Windows.Controls.Button> elemento y, a continuación, haga clic en **navegar hasta el controlador de eventos**.

     Este paso abre *DataControl. Xaml. CS* y crea un controlador de código auxiliar para el `Button_Click` evento.

2. Agregue las siguientes `using` directivas a la parte superior del archivo.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs" id="Snippet11":::

3. Agregue una `SettingsStore` propiedad privada, como se muestra en el ejemplo siguiente.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Esta propiedad obtiene primero una referencia a la <xref:EnvDTE80.DTE2> interfaz, que contiene el modelo de objetos de automatización, del <xref:System.Windows.FrameworkElement.DataContext%2A> control de usuario y, a continuación, usa el objeto DTE para obtener una instancia de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interfaz. A continuación, utiliza esa instancia para devolver la configuración del usuario actual.

4. Rellene el `Button_Click` evento como se indica a continuación.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     Esto escribe el contenido del cuadro de texto en un campo "mi configuración" en una colección "Configurations" en el registro. Si la colección no existe, se crea.

5. Agregue el siguiente controlador para el `OnLoaded` evento del control de usuario.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Este código establece el texto del cuadro de texto en el valor actual de "mi valor".

6. Cree el control de usuario.

7. En **Explorador de soluciones**, Abra *source. Extension. vsixmanifest*.

8. En el editor de manifiestos, establezca **el nombre del producto** en la **Página de inicio de guardar mi configuración**.

     Esta característica establece el nombre de la página de inicio como aparece en la lista **Personalizar Página de inicio** del cuadro de diálogo **Opciones** .

9. Cree *StartPage. Xaml*.

## <a name="test-the-control"></a>Prueba del control

1. Presione **F5**.

     Se abre la instancia experimental de Visual Studio.

2. En la instancia experimental, en el menú **herramientas** , haga clic en **Opciones**.

3. En el nodo **entorno** , haga clic en **Inicio** y, a continuación, en la lista **Personalizar Página de inicio** , seleccione **[extensión instalada] guardar la página de inicio** de la configuración.

     Haga clic en **OK**.

4. Cierre la página de inicio si está abierta y, a continuación, en el menú **Ver** , haga clic en **Página de inicio**.

5. En la página Inicio, haga clic en la pestaña **control** .

6. En el cuadro de texto, escriba **CAT** y, a continuación, haga clic en **guardar mi configuración**.

7. Cierre la página de inicio y vuelva a abrirla.

     La palabra "cat" se debe mostrar en el cuadro de texto.

8. Reemplace la palabra "cat" por la palabra "Dog". No haga clic en el botón.

9. Cierre la página de inicio y vuelva a abrirla.

     La palabra "Dog" se debe mostrar en el cuadro de texto, aunque no se haya guardado la configuración porque Visual Studio mantiene las ventanas de herramientas en memoria, incluso si están cerradas, hasta que Visual Studio se cierra.

10. Cierre la instancia experimental de Visual Studio.

11. Presione **F5** para volver a abrir la instancia experimental.

12. La palabra "cat" se debe mostrar en el cuadro de texto.

## <a name="next-steps"></a>Pasos siguientes

Puede modificar este control de usuario para guardar y recuperar cualquier número de valores de configuración personalizados mediante el uso de diferentes valores de controladores de eventos diferentes para obtener y establecer la `SettingsStore` propiedad. Siempre que use un `propertyName` parámetro diferente para cada llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , los valores no se sobrescriben entre sí en el registro.

## <a name="see-also"></a>Consulte también

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
