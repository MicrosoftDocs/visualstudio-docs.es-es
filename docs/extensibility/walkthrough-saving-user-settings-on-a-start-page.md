---
title: 'Tutorial: Guardar la configuración de usuario en una página de inicio ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697075"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Tutorial: Guardar la configuración de usuario en una página de inicio

Puede conservar la configuración de usuario de la página de inicio. Siguiendo este tutorial, puede crear un control que guarde una configuración en el registro cuando el usuario hace clic en un botón y, a continuación, recupera esa configuración cada vez que se carga la página de inicio. Dado que la plantilla de proyecto de página de inicio incluye un control de usuario personalizable y el XAML de página de inicio predeterminado llama a ese control, no es que se debe modificar la propia página de inicio.

El almacén de configuración que se crea <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> una instancia en este tutorial es una instancia de la interfaz, que lee y escribe en la siguiente ubicación del Registro cuando se llama: **HKCU, Software, Microsoft, VisualStudio, 14.0\\\<CollectionName>**

Cuando se ejecuta en la instancia experimental de Visual Studio, el almacén de configuración lee y escribe en **HKCU, Software, Microsoft, VisualStudio, 14,0Exp,\\\<CollectionName>.**

Para obtener más información sobre cómo conservar la configuración, consulte [Ampliación](../extensibility/extending-user-settings-and-options.md)de la configuración y las opciones de usuario .

## <a name="prerequisites"></a>Prerrequisitos

> [!NOTE]
> Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).
>
> Puede descargar la plantilla de proyecto de página de inicio mediante **el Administrador de extensiones**.

## <a name="set-up-the-project"></a>Configuración del proyecto

1. Cree un proyecto de página de inicio como se describe en [Crear una página](creating-a-custom-start-page.md)de inicio personalizada . Asigne al proyecto el nombre **SaveMySettings**.

2. En el Explorador de **soluciones**, agregue las siguientes referencias de ensamblado al proyecto StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Abra *MyControl.xaml*.

4. En el panel XAML, en <xref:System.Windows.Controls.UserControl> la definición de elemento de nivel superior, agregue la siguiente declaración de evento después de las declaraciones de espacio de nombres.

    ```xml
    Loaded="OnLoaded"
    ```

5. En el panel de diseño, haga clic en el área principal del control y, a continuación, presione **Eliminar**.

     Este paso quita <xref:System.Windows.Controls.Border> el elemento y todo lo que <xref:System.Windows.Controls.Grid> contiene, y deja solo el elemento de nivel superior.

6. Desde el cuadro <xref:System.Windows.Controls.StackPanel> de **herramientas**, arrastre un control a la cuadrícula.

7. Ahora arrastre <xref:System.Windows.Controls.TextBlock>un <xref:System.Windows.Controls.TextBox>, un , <xref:System.Windows.Controls.StackPanel>y un botón al archivo .

8. Agregue un atributo **x:Name** para el <xref:System.Windows.Controls.TextBox>archivo , y un `Click` evento para el <xref:System.Windows.Controls.Button>, como se muestra en el ejemplo siguiente.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementar el control de usuario

1. En el panel XAML, `Click` haga clic <xref:System.Windows.Controls.Button> con el botón secundario en el atributo del elemento y, a continuación, haga clic en **Navegar al controlador de eventos**.

     Este paso abre *MyControl.xaml.cs*y crea un `Button_Click` controlador de código auxiliar para el evento.

2. Agregue las `using` siguientes directivas a la parte superior del archivo.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

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

     Esta propiedad primero obtiene una <xref:EnvDTE80.DTE2> referencia a la interfaz, <xref:System.Windows.FrameworkElement.DataContext%2A> que contiene el modelo de objetos Automation, desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> el control de usuario y, a continuación, usa el DTE para obtener una instancia de la interfaz. A continuación, utiliza esa instancia para devolver la configuración de usuario actual.

4. Rellene el `Button_Click` evento de la siguiente manera.

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

     Esto escribe el contenido del cuadro de texto en un campo "MySetting" en una colección "MySettings" en el registro. Si la colección no existe, se crea.

5. Agregue el siguiente `OnLoaded` controlador para el evento del control de usuario.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Este código establece el texto del cuadro de texto en el valor actual de "MySetting".

6. Compile el control de usuario.

7. En **el Explorador**de soluciones , abra *source.extension.vsixmanifest*.

8. En el editor de manifiestos, establezca **Nombre del producto** en Guardar la página de inicio de la **configuración**.

     Esta característica establece el nombre de la página de inicio tal como debe aparecer en la lista **Personalizar página** de inicio del cuadro de diálogo **Opciones.**

9. Compile *StartPage.xaml*.

## <a name="test-the-control"></a>Prueba del control

1. Presione **F5**.

     Se abre la instancia experimental de Visual Studio.

2. En la instancia experimental, en el menú **Herramientas,** haga clic en **Opciones**.

3. En el nodo **Entorno** , haga clic en **Inicio**y, a continuación, en la lista Personalizar página de **inicio,** seleccione **[Extensión instalada] Guardar mi página**de inicio de configuración .

     Haga clic en **OK**.

4. Cierre la página de inicio si está abierta y, a continuación, en el menú **Ver,** haga clic en **Página de inicio**.

5. En la página de inicio, haga clic en la pestaña **MyControl.**

6. En el cuadro de texto, escriba **Cat**y, a continuación, haga clic en **Guardar mi configuración**.

7. Cierre la página de inicio y, a continuación, vuelva a abrirla.

     La palabra "Gato" debe mostrarse en el cuadro de texto.

8. Reemplace la palabra "Cat" por la palabra "Dog". No haga clic en el botón.

9. Cierre la página de inicio y, a continuación, vuelva a abrirla.

     La palabra "Perro" debe mostrarse en el cuadro de texto, aunque no haya guardado la configuración porque Visual Studio mantiene las ventanas de herramientas en la memoria, incluso si están cerradas, hasta que Visual Studio se cierra.

10. Cierre la instancia experimental de Visual Studio.

11. Presione **F5** para volver a abrir la instancia experimental.

12. La palabra "Gato" debe mostrarse en el cuadro de texto.

## <a name="next-steps"></a>Pasos siguientes

Puede modificar este control de usuario para guardar y recuperar cualquier número de valores personalizados mediante el uso de valores diferentes de diferentes controladores de eventos para obtener y establecer la `SettingsStore` propiedad. Siempre que use un `propertyName` parámetro diferente <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>para cada llamada a , los valores no se sobrescriben entre sí en el registro.

## <a name="see-also"></a>Vea también

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
