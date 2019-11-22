---
title: Probar aplicaciones para UWP y Windows Phone 8.1 con pruebas automatizadas de IU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f2ac13b62dcc522626fde92b1b29cac9873edec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301831"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Probar aplicaciones para UWP y Windows Phone 8.1 con pruebas automatizadas de IU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use este tutorial para crear pruebas de IU para aplicaciones para UWP que se ejecutan en dispositivos móviles o emuladores, y para aplicaciones de Windows Phone 8.1 basadas en XAML.

## <a name="create-a-simple-windows-phone-app"></a>Crear una aplicación simple de Windows Phone

1. Cree un nuevo proyecto para una aplicación de Windows Phone vacía mediante una plantilla de Visual C# o Visual Basic.

     ![Create a new Windows Phone app](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")

2. En el Explorador de soluciones, abra el archivo MainPage.xaml. Desde el Cuadro de herramientas, arrastre un control de botón y un control de cuadro de texto a la superficie de diseño.

     ![Add contols to MainPage.xaml](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")

3. En la ventana Propiedades, asigne un nombre al control de botón.

     ![Name the button control](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")

4. Asigne un nombre al control del cuadro de texto.

     ![Name the textbox control](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")

5. En la superficie del diseñador, haga doble clic en el control de botón y agregue el código siguiente:

    ```csharp
    private void button_Click_1(object sender, RoutedEventArgs e)
    {
        this.textBox.Text = this.button.Name;
    }

    ```

    ```vb
    Public NotInheritable Class MainPage
        Inherits Page

        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click
            Me.textBox.Text = Me.button.Name
        End Sub
    End Class
    ```

6. Presione F5 para ejecutar la aplicación de Windows Phone en el emulador y comprobar si está funcionando.

     ![Run the Windows Phone app](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")

7. Salga del emulador.

## <a name="deploy-the-windows-phone-app"></a>Implementar la aplicación de Windows Phone

1. Para que la prueba de interfaz de usuario codificada pueda asignar controles de una aplicación, debe implementar la aplicación.

     ![Deploy the Windows Phone app](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")

     El emulador se inicia. La aplicación ya está disponible para probarla.

     ![App deployed on emulator](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")

     Mantenga el emulador ejecutándose mientras crea la prueba de interfaz de usuario codificada.

## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Crear una prueba de interfaz de usuario codificada para la aplicación de Windows Phone

[¿Cómo puedo crear pruebas automatizadas de IU para aplicaciones de la Plataforma universal de Windows (UWP)?](#uwpapps)

1. Agregue un nuevo proyecto de prueba de interfaz de usuario codificada a la solución con la aplicación de Windows Phone.

    ![Create new coded UI  test for Windows Phone](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")

2. Elija editar la asignación de IU mediante la herramienta de selección precisa.

    ![Generate coded UI test using cross&#45;hair tool.](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")

3. Utilice la herramienta de selección precisa para seleccionar la aplicación y luego copie el valor de la propiedad **AutomationId** de la aplicación, que se usará después para iniciar la aplicación en la prueba.

    ![Copy the app's AutomationId value](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")

4. En el emulador, inicie la aplicación y use la herramienta de selección precisa para elegir el control de botón. Después, agregue el control de botón a la asignación de controles de interfaz de usuario.

    ![Use the cross&#45;hair tool to map controls](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")

5. Para agregar el control de cuadro de texto a la asignación de control de interfaz de usuario, repita el paso anterior.

    ![Use the cross&#45;hair tool and map textbox control](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")

6. Elija Generar código para crear código para los cambios en la asignación de controles de interfaz de usuario.

    ![Generate code from the builder](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")

7. Utilice la herramienta de selección precisa para seleccionar el control de cuadro de texto y después seleccione la propiedad **Texto** .

    ![Select the Text property](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")

8. Agregue una aserción. Se utilizará en la prueba para comprobar que el valor sea correcto.

    ![Add assertion to the test](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")

9. Agregue y genere código para el método de aserción.

     ![Generate code for the assertion](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")

10. **Visual C#**

     En el Explorador de soluciones, abra el archivo UIMap.Designer.cs para ver el código recién agregado para el método de aserción y los controles.

     **Visual Basic**

     En el Explorador de soluciones, abra el archivo CodedUITest1.vb. En el código del método de prueba CodedUITestMethod1(), haga clic con el botón secundario en la llamada al método de aserción que se agregó automáticamente, `Me.UIMap.AssertMethod1()` , y elija **Ir a definición**. Esto abrirá el archivo de UIMap.Designer.vb en el editor de código, de modo que pueda ver el código agregado para el método de aserción y los controles.

    > [!WARNING]
    > No modifique directamente el archivo UIMap.designer.cs o el archivo UIMap.Designer.vb. Si lo hace, se sobrescribirán los cambios en el archivo cada vez que se genere la prueba.

     **Método de aserción**

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp1Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)
    End Sub
    ```

     **Controles**

    ```csharp
    #region Properties
    public virtual AssertMethod1ExpectedValues AssertMethod1ExpectedValues
    {
        get
        {
            if ((this.mAssertMethod1ExpectedValues == null))
            {
                this.mAssertMethod1ExpectedValues = new AssertMethod1ExpectedValues();
            }
            return this.mAssertMethod1ExpectedValues;
        }
    }

    public UIApp1Window UIApp1Window
    {
        get
        {
            if ((this.mUIApp1Window == null))
            {
                this.mUIApp1Window = new UIApp1Window();
            }
            return this.mUIApp1Window;
        }
    }
    #endregion

    #region Fields
    private AssertMethod1ExpectedValues mAssertMethod1ExpectedValues;

    private UIApp1Window mUIApp1Window;
    #endregion
    ```

    ```vb
    #Region "Properties"
    Public ReadOnly Property UIButtonButton() As XamlButton
        Get
            If (Me.mUIButtonButton Is Nothing) Then
                Me.mUIButtonButton = New XamlButton(Me)
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"
            End If
            Return Me.mUIButtonButton
        End Get
    End Property

    Public ReadOnly Property UITextBoxEdit() As XamlEdit
        Get
            If (Me.mUITextBoxEdit Is Nothing) Then
                Me.mUITextBoxEdit = New XamlEdit(Me)
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"
            End If
            Return Me.mUITextBoxEdit
        End Get
    End Property
    #End Region

    #Region "Fields"
    Private mUIButtonButton As XamlButton

    Private mUITextBoxEdit As XamlEdit
    #End Region
    ```

11. En el Explorador de soluciones, abra el archivo CodedUITest1.cs o CodedUITest1.vb. Ahora puede agregar código al método CodedUTTestMethod1 para las acciones necesarias para ejecutar la prueba. Use los controles agregados a UIMap para agregar código:

    1. Inicie la aplicación de Windows Phone mediante la propiedad ID de automatización que copió al Portapapeles previamente:

       ```csharp
       XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

       ```vb
       XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

    2. Agregue un gesto para pulsar el control de botón:

       ```csharp
       Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);
       ```

       ```vb
       Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)
       ```

    3. Compruebe que la llamada al método de aserción que se generó automáticamente se incluye después de iniciar la aplicación y el gesto en el botón:

       ```csharp
       this.UIMap.AssertMethod1();
       ```

       ```vb
       Me.UIMap.AssertMethod1()
       ```

       Tras agregar el código, el método de prueba CodedUITestMethod1 debería ser similar al siguiente:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.

        // Launch the app.
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");

        // Tap the button.
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);

        this.UIMap.AssertMethod1();
    }
    ```

    ```vb
    <CodedUITest>
    Public Class CodedUITest1

        <TestMethod()>
        Public Sub CodedUITestMethod1()
            '
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
            '
            ' Launch the app.
            XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App")

            '// Tap the button.
            Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)

            Me.UIMap.AssertMethod1()
        End Sub
    ```

## <a name="run-the-coded-ui-test"></a>Ejecutar la prueba de interfaz de usuario codificada

1. Compile la prueba y luego ejecútela mediante el explorador de pruebas.

     ![Build and run the test using Test Explorer](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")

     La aplicación de Windows Phone se inicia, la acción para pulsar el botón se completa y la propiedad Text del cuadro de texto se rellena y se valida mediante el método de aserción.

     ![Running Winodws Phone test](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")

     Una vez finalizada la prueba, el explorador de pruebas confirma que se superó la prueba.

     ![Test Explorer results](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")

## <a name="TestingPhoneAppsCodedUI_DataDriven"></a> Usar pruebas de interfaz de usuario codificadas controladas por datos en las aplicaciones de Windows Phone
 Para probar las distintas condiciones, se puede ejecutar varias veces una prueba de interfaz de usuario codificada con distintos conjuntos de datos.

 Las pruebas de interfaz de usuario codificadas controladas por datos para Windows Phone se definen mediante el atributo DataRow en un método de prueba. En el siguiente ejemplo, x e y usan los valores 1 y 2 para la primera iteración y -1 y -2 para la segunda iteración de la prueba.

```
[DataRow(1, 2, DisplayName = "Add positive numbers")]
[DataRow(-1, -2, DisplayName = "Add negative numbers")]
[TestMethod]
public void DataDrivingDemo_MyTestMethod(int x, int y)

```

## <a name="q--a"></a>Preguntas y respuestas

### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>P: ¿Tengo que implementar la aplicación de Windows Phone en el emulador para asignar los controles de interfaz de usuario?
 **R**: Sí. El generador de pruebas de interfaz de usuario codificadas exige que se esté ejecutando un emulador y que la aplicación esté implementada en él. De lo contrario, mostrará un mensaje de error que indicará que no se encuentra ningún emulador en ejecución.

### <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a> P: ¿Se puede ejecutar las pruebas solo en el emulador o puedo también usar un dispositivo físico?
 **R**: Se admiten ambas opciones. El destino de la ejecución de prueba se selecciona cambiando el tipo de emulador o seleccionando el dispositivo en la barra de herramientas del dispositivo. Si se seleccionó Dispositivo, tiene que haber un dispositivo Phone Blue conectado a uno de los puertos USB de la máquina.

 ![Select the emulator version, or physcial device](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>P: ¿Por qué no veo la opción para registrar la prueba de IU codificada en la opción Generar código de un cuadro de diálogo Prueba de IU codificada?
 **R**: La opción para registrar no se admite en aplicaciones de Windows Phone.

### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>P: ¿Puedo crear una prueba de interfaz de usuario codificada para las aplicaciones de Windows Phone basadas en WinJS, Silverlight o HTML5?
 **R**: No. Solo se admiten aplicaciones basadas en XAML.

### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>P: ¿Puedo crear pruebas de IU codificadas para las aplicaciones de Windows Phone en un sistema que no ejecute Windows 8.1 ni Windows 10?
 **R**: No, las plantillas de proyecto de prueba de IU codificada solo están disponibles en Windows 8.1 y Windows 10. Para crear la automatización para las aplicaciones de la Plataforma universal de Windows (UWP), necesitará Windows 10.

<a name="uwpapps"></a>
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>P: ¿Cómo puedo crear pruebas de IU codificadas para las aplicaciones de la Plataforma universal de Windows (UWP)?
 **R**: Según la plataforma en la que vaya a probar su aplicación para UWP, cree el proyecto de prueba de IU codificada de una de estas maneras:

- Una aplicación para UWP que se ejecuta en el equipo local se ejecutará como una aplicación de la Tienda. Para probarlo, debe usar la plantilla **Proyecto de prueba de IU codificada (Windows)** . Para encontrar esta plantilla cuando cree un nuevo proyecto, vaya al nodo **Windows**, **Universal** . O vaya al nodo **Windows**, **Windows 8**, **Windows** .

- Una aplicación para UWP que se ejecute en el dispositivo o emulador se ejecutará como una aplicación de Windows Phone. Para probarlo, debe usar la plantilla **Proyecto de prueba de IU codificada (Windows Phone)** . Para encontrar esta plantilla cuando cree un nuevo proyecto, vaya al nodo **Windows**, **Universal** . O vaya al nodo **Windows**, **Windows 8**, **Windows Phone** .

  Después de crear el proyecto, el procedimiento para crear una prueba sigue siendo el mismo que antes.

### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>P: ¿Puedo seleccionar controles externos al emulador?
 **R**: No. El compilador no los detectará.

### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>P: ¿Puedo usar el compilador de pruebas de interfaz de usuario codificadas para asignar controles mediante un dispositivo telefónico fijo?
 **R**: No. El compilador solo puede asignar elementos de la interfaz de usuario si la aplicación se implementó en el emulador.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>P: ¿Por qué no puedo modificar el código en el archivo UIMap.Designer?
 **R:** Cualquier cambio que se efectúe en el código del archivo UIMapDesigner.cs se sobrescribirá cada vez que se genere código mediante UIMap - Generador de pruebas de IU codificadas. Si tiene que modificar un método grabado, debe copiarlo en el archivo UIMap.cs y cambiar el nombre. El archivo UIMap.cs se puede utilizar para invalidar métodos y propiedades en el archivo UIMapDesigner.cs. Debe quitar la referencia al método original en el archivo UITest.cs el Codificado y reemplazarlo con el nombre del método cuyo nombre ha cambiado.

### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>P: ¿Puedo ejecutar una prueba de interfaz de usuario codificada en mi aplicación de Windows Phone desde la línea de comandos?
 **R**: Sí. Use un archivo runsettings para especificar el dispositivo de destino para la ejecución de prueba. Por ejemplo:

 **vstest.console.exe “pathToYourCodedUITestDll” /settings:devicetarget.runsettings**

 Archivo de ejemplo runsettings:

```
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
<MSPhoneTest>
<!--to specify test execution on device, use a TargetDevice option as follows-->
<TargetDevice>Device</TargetDevice>
<!--to specify an emulator instead, use a TargetDevice option like below-->
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->
</MSPhoneTest>
</RunSettings>
```

### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>P: ¿Cuáles son las diferencias entre las pruebas de interfaz de usuario codificadas para las aplicaciones de Windows Store basadas en XAML y las aplicaciones de Windows Phone?
 **R**: Debajo se indican algunas de las diferencias clave:

|Característica|Aplicaciones de la Tienda Windows|Aplicaciones de Windows Phone|
|-------------|------------------------|------------------------|
|Destino para ejecutar las pruebas|Equipo local o remoto. Se pueden especificar equipos remotos cuando use un caso de prueba automatizado para ejecutar las pruebas. Vea [Automatizar un caso de prueba en Microsoft Test Manager](https://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Emulador o dispositivo. Vea [P: ¿Se puede ejecutar las pruebas solo en el emulador o puedo también usar un dispositivo físico?](#TestingPhoneAppsCodedUI_EmulatorDevice) en este tema.|
|Ejecutar desde la línea de comandos|El archivo de configuración no es necesario para especificar el destino.|El archivo Runsettings es necesario para especificar el destino.|
|Clases especializadas para controles de shell|[DirectUIControl](/previous-versions/dn248208(v=vs.140))|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|
|Control WebView en una aplicación XAML|Admitido si usa clases Html* especializadas para interactuar con elementos HTML. Consulte <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|No se admite.|
|Ejecutar pruebas automatizadas desde MTM|Se admite.|No se admite.|
|Pruebas controladas por datos|Vea [Pruebas controladas por datos](../test/creating-a-data-driven-coded-ui-test.md) para información sobre el uso de orígenes de datos externos y el uso del atributo DataSource en un método de prueba.|Los datos se especifican en línea, con el atributo DataRow en un método de prueba. Vea [Usar pruebas de interfaz de usuario codificadas controladas por datos en las aplicaciones de Windows Phone](#TestingPhoneAppsCodedUI_DataDriven) en este tema.|

## <a name="external-resources"></a>Recursos externos
 Blog de administración del ciclo de vida de las aplicaciones de Microsoft Visual Studio: [Uso de interfaces de usuario codificadas para probar aplicaciones de Windows Phone basadas en XAML](https://devblogs.microsoft.com/devops/using-coded-ui-to-test-xaml-based-windows-phone-apps/#comments)

## <a name="see-also"></a>Vea también
 [Usar Automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
