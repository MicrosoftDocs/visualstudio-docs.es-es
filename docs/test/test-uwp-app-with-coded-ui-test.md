---
title: Probar una aplicación de UWP con una prueba automatizada de IU
ms.date: 05/31/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: fdd3d98bd848bb6fe679809a58f2e316a316f012
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590363"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Crear una prueba automatizada de IU para probar una aplicación de UWP

En este artículo se explica cómo crear una prueba automatizada de IU para una aplicación de la Plataforma universal de Windows (UWP).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Crear la aplicación de UWP que se va a probar

El primer paso es crear una aplicación sencilla de UWP para ejecutar la prueba.

1. En Visual Studio, cree un nuevo proyecto con la plantilla **Aplicación vacía (Windows Universal)** para Visual C# o Visual Basic.

   ::: moniker range="vs-2017"

   ![Plantilla de aplicación vacía de Windows Universal](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. En el cuadro de diálogo **Nuevo proyecto de la plataforma universal de Windows**, seleccione **Aceptar** para aceptar las versiones de la plataforma predeterminadas.

1. En el **Explorador de soluciones**, abra *MainPage.xaml*.

   El archivo se abre en el **Diseñador XAML**.

1. Arrastre un control de botón y un control de cuadro de texto desde el **Cuadro de herramientas** a la superficie de diseño.

     ![Diseñar la aplicación de UWP](../test/media/toolbox-controls.png)

1. Asigne nombres a los controles. Seleccione el control de cuadro de texto y, después, en la ventana **Propiedades**, escriba **textBox** en el campo **Nombre**. Seleccione el control de botón y, después, en la ventana **Propiedades**, escriba **button** en el campo **Nombre**.

1. Haga doble clic en el control de botón y agregue el código siguiente al cuerpo del método `Button_Click`. Este código simplemente establece el texto del cuadro de texto en el nombre del control de botón, con el único propósito de realizar una comprobación con la prueba automatizada de IU que crearemos más adelante.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Presione **Ctrl**+**F5** para ejecutar la aplicación. Debería ver algo parecido a lo siguiente:

   ![Aplicación de UWP con botón y cuadro de texto](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Crear una prueba de IU codificada

1. Para agregar un nuevo proyecto de prueba a la solución, haga clic con el botón derecho en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

1. Busque la plantilla de proyecto **Proyecto de prueba automatizada de IU (Windows universal)** y selecciónela.

   ::: moniker range="vs-2017"

   ![Nuevo proyecto de prueba automatizada de IU](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Si no ve la plantilla **Proyecto de prueba automatizada de IU (Windows universal)** , necesitará [instalar el componente de prueba automatizada de IU](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. En el cuadro de diálogo **Generar código para prueba automatizada de IU**, seleccione **Editar la prueba manualmente**.

   ![Generar código para prueba automatizada de IU](../test/media/manually-edit-the-test.png)

1. Si su aplicación de UWP no se está ejecutando, presione **Ctrl**+**F5** para iniciarla.

1. Abra el cuadro de diálogo **Generador de pruebas automatizadas de IU** colocando el cursor en el método `CodedUITestMethod1` y, después, elija **Prueba** > **Generar código para prueba automatizada de IU** > **Usar Generador de pruebas automatizadas de IU**.

1. Agregue los controles a la asignación de controles de interfaz de usuario. Use la herramienta de selección precisa del **Generador de pruebas automatizadas de IU** para seleccionar el control de botón en la aplicación de UWP. En el cuadro de diálogo **Agregar aserciones**, expanda el panel **Asignación de controles de IU** si es necesario y, después, seleccione **Agregar control a Asignación de controles de IU**.

     ![Agregar control a la asignación de IU](../test/media/add-control-to-ui-control-map.png)

1. Para agregar el control de cuadro de texto a la asignación de control de interfaz de usuario, repita el paso anterior.

1. En el **Generador de pruebas automatizadas de IU**, seleccione **generar código** o presione **Ctrl**+**G**. A continuación, seleccione **Generar** para crear código para los cambios en la asignación de controles de interfaz de usuario.

     ![Generar código para la asignación de IU](../test/media/generate-code-dialog.png)

1. Para comprobar que el texto del cuadro de texto cambia a **botón** cuando se hace clic en el botón, haga clic en el botón.

     ![Hacer clic en el control de botón para establecer el valor del cuadro de texto](../test/media/uwp-app-button-textbox.png)

1. Agregue una aserción para comprobar el texto del control de cuadro de texto. Utilice la herramienta de selección precisa para seleccionar el control de cuadro de texto y después seleccione la propiedad **Texto** en el cuadro de diálogo **Agregar aserciones**. A continuación, seleccione **Agregar aserción** o presione **Alt**+**A**. En el cuadro **Mensaje sobre el error de aserción**, escriba **No se esperaba el valor del cuadro de texto.** A continuación, seleccione **Aceptar**.

     ![Elegir cuadro de texto con selección precisa y agregar aserción](../test/media/add-assertion-for-text.png)

1. Genere el código de prueba para la aserción. En el cuadro de diálogo **Generador de pruebas automatizadas de IU**, seleccione **Generar código**. En el cuadro de diálogo **Generar código**, seleccione **Agregar y generar**.

     ![Generar código para la aserción del cuadro de texto](../test/media/add-and-generate-assert-method.png)

   En el **Explorador de soluciones**, abra *UIMap.Designer.cs* para ver el código agregado para el método de aserción y los controles.

   > [!TIP]
   > Si está utilizando Visual Basic, abra *CodedUITest1.vb*. A continuación, en el código del método de prueba `CodedUITestMethod1()`, haga con el botón derecho en la llamada al método de aserción `Me.UIMap.AssertMethod1()` y elija **Ir a definición**. *UIMap.Designer.vb* se abre en el editor de código para que pueda ver el código agregado para el método de aserción y los controles.

    > [!WARNING]
    > No modifique directamente los archivos *UIMap.designer.cs* o *UIMap.Designer.vb*. Si lo hace, se sobrescribirán los cambios cuando se genere la prueba.

    El método de aserción tiene el siguiente aspecto:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. A continuación, se necesita obtener el identificador **AutomationId** de la [aplicación](#create-a-uwp-app-to-test) de UWP que se va a probar. Abra el menú **Inicio** de Windows para ver el icono de la aplicación. A continuación, arrastre la herramienta de selección precisa ![Icono de destino](media/target-icon.png) desde el cuadro de diálogo **Generador de pruebas automatizadas de IU** al icono de la aplicación. Cuando un cuadro azul rodee el icono, suelte el mouse.

   ![Herramienta de selección precisa](media/cross-hair-tool.png)

   El cuadro de diálogo **Agregar aserciones** se abre y muestra el **AutomationId** de la aplicación. Haga clic con el botón derecho en **AutomationId** y seleccione **Copiar valor en el portapapeles**.

   ![AutomationID en el cuadro de diálogo Agregar aserción](../test/media/automation-id.png)

1. Agregue código al método de prueba para iniciar la aplicación de UWP. En el **Explorador de soluciones**, abra el archivo *CodedUITest1.cs* o *CodedUITest1.vb*. Por encima de la llamada a `AssertMethod1`, agregue código para iniciar la aplicación de UWP:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Reemplace el identificador de automatización en el código de ejemplo por el valor que copió en el portapapeles en el paso anterior.

   > [!IMPORTANT]
   > Recorte el principio del identificador de automatización para quitar caracteres como **P ~** . Si no recorta estos caracteres, la prueba produce una `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` al intentar iniciar la aplicación.

1. A continuación, agregue código al método de prueba para hacer clic en el botón. En la línea siguiente a `XamlWindow.Launch`, agregue un gesto para pulsar el control de botón:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Tras agregar el código, el método de prueba `CodedUITestMethod1` completo debería ser similar al siguiente:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Compile el proyecto de prueba y, después, seleccione **Probar** > **Windows** > **Explorador de pruebas** para abrir el **Explorador de pruebas**.

1. Seleccione **Ejecutar todo** para ejecutar la prueba.

   La aplicación se abre, el botón se pulsa y la propiedad **Texto** del cuadro de texto se rellena. El método de aserción valida la propiedad **Texto** del cuadro de texto.

   Una vez completada la prueba, el **Explorador de pruebas** confirma que se superó la prueba.

   ![La prueba superada se muestra en el Explorador de pruebas](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Preguntas y respuestas

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>P: ¿Por qué no veo la opción para registrar la prueba automatizada de IU en la opción Generar código de un cuadro de diálogo Prueba automatizada de IU?

**R**: La opción para registrar no se admite en las aplicaciones para UWP.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>P: ¿Puedo crear una prueba automatizada de IU para las aplicaciones para UWP basadas en WinJS?

**R**: No. Solo se admiten aplicaciones basadas en XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>P: ¿Por qué no puedo modificar el código en el archivo UIMap.Designer?

**R**: Cualquier cambio que se efectúe en el código del archivo *UIMapDesigner.cs* se sobrescribe cada vez que se genera código mediante el **Generador de pruebas automatizadas de IU**. Si tiene que modificar un método grabado, cópielo en el archivo *UIMap.cs* y cámbiele el nombre. El archivo *UIMap.cs* se puede utilizar para invalidar métodos y propiedades en el archivo *UIMapDesigner.cs*. Quite la referencia al método original en el archivo *CodedUITest.cs* y reemplácelo por el nombre del método cuyo nombre ha cambiado.

## <a name="see-also"></a>Vea también

- [Usar la automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Establecer una propiedad única de automatización para controles UWP para pruebas](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
