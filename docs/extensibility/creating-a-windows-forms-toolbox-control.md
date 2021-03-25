---
title: Crear un control Windows Forms Toolbox | Microsoft Docs
description: En este tutorial se muestra cómo usar la plantilla de control de cuadro de herramientas de Windows Forms para crear un control de contador simple mediante el SDK de Visual Studio.
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42dcf30e7c31880357bb95e3858a2c70aa59f174
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089334"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Crear un control de cuadro de herramientas de Windows Forms

La plantilla de elemento de control de cuadro de herramientas Windows Forms que se incluye en el Herramientas de extensibilidad de Visual Studio (SDK de VS) le permite crear un control de **cuadro de herramientas** que se agrega automáticamente cuando se instala la extensión. En este tutorial se muestra cómo usar la plantilla para crear un control de contador simple que se puede distribuir a otros usuarios.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Crear el control Toolbox

La plantilla de control de cuadro de herramientas de Windows Forms crea un control de usuario no definido y proporciona todas las funciones necesarias para agregar el control al **cuadro de herramientas**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Crear una extensión con un control de cuadro de herramientas Windows Forms

1. Cree un proyecto VSIX denominado `MyWinFormsControl` . Puede encontrar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , mediante la búsqueda de "VSIX".

2. Cuando se abra el proyecto, agregue una plantilla de elemento de **control de cuadro de herramientas Windows Forms** denominada `Counter` . En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a extensibilidad de **Visual C#**  >   y seleccione **Windows Forms control Toolbox**

3. Esto agrega un control de usuario, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> para colocar el control en el **cuadro de herramientas** y una entrada de recurso **Microsoft. VisualStudio. TOOLBOXCONTROL** en el manifiesto de VSIX para la implementación.

### <a name="build-a-user-interface-for-the-control"></a>Compilar una interfaz de usuario para el control

El `Counter` control requiere dos controles secundarios: un <xref:System.Windows.Forms.Label> para mostrar el recuento actual y un <xref:System.Windows.Forms.Button> para restablecer el recuento en 0. No se requieren otros controles secundarios, ya que los llamadores incrementarán el contador mediante programación.

#### <a name="to-build-the-user-interface"></a>Para crear la interfaz de usuario

1. En **Explorador de soluciones**, haga doble clic en *Counter. CS* para abrirlo en el diseñador.

2. Quite el **clic aquí.** que se incluye de forma predeterminada al agregar la plantilla de elemento de control de cuadro de herramientas Windows Forms.

3. En el **cuadro de herramientas**, arrastre un `Label` control y, a continuación, un `Button` control situado debajo de él a la superficie de diseño.

4. Cambie el tamaño del control de usuario general a 150, 50 píxeles, y cambie el tamaño del control de botón a 50, 20 píxeles.

5. En la ventana **propiedades** , establezca los siguientes valores para los controles en la superficie de diseño.

    |Control|Propiedad|Value|
    |-------------|--------------|-----------|
    |`Label1`|**Texto**|""|
    |`Button1`|**Nombre**|btnReset|
    |`Button1`|**Texto**|Reset|

### <a name="code-the-user-control"></a>Codificar el control de usuario

El `Counter` control expondrá un método para incrementar el contador, un evento que se va a generar cada vez que se incrementa el contador, un botón de **restablecimiento** y tres propiedades para almacenar el recuento actual, el texto para mostrar y si se debe mostrar u ocultar el botón de **restablecimiento** . El atributo `ProvideToolboxControl` determina la ubicación del **Cuadro de herramientas** donde se mostrará el control `Counter` .

#### <a name="to-code-the-user-control"></a>Para codificar el control de usuario

1. Haga doble clic en el formulario para abrir el controlador de eventos de carga en la ventana de código.

2. Encima del método de controlador de eventos, en la clase control, cree un entero para almacenar el valor del contador y una cadena para almacenar el texto para mostrar como se muestra en el ejemplo siguiente.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Cree las siguientes declaraciones de propiedades públicas.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Los llamadores pueden tener acceso a estas propiedades para obtener y establecer el texto para mostrar del contador y para mostrar u ocultar el botón **restablecer** . Los llamadores pueden obtener el valor actual de la propiedad de solo lectura `Value` , pero no pueden establecer el valor directamente.

4. Coloque el código siguiente en el `Load` evento para el control.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Establecer el texto de la **etiqueta** en el <xref:System.Windows.Forms.UserControl.Load> evento permite que se carguen las propiedades de destino antes de que se apliquen sus valores. Establecer el texto de la **etiqueta** en el constructor daría como resultado una **etiqueta** vacía.

5. Cree el siguiente método público para incrementar el contador.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Agregue una declaración para el `Incremented` evento a la clase del control.

    ```csharp
    public event EventHandler Incremented;
    ```

    Los llamadores pueden agregar controladores a este evento para responder a los cambios en el valor del contador.

7. Vuelva a la vista de diseño y haga doble clic en el botón **restablecer** para generar el `btnReset_Click` controlador de eventos. A continuación, rellénelo como se muestra en el ejemplo siguiente.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Justo encima de la definición de clase en la declaración de atributos de `ProvideToolboxControl` , cambie el valor del primer parámetro de `"MyWinFormsControl.Counter"` a `"General"`. Se establece el nombre del grupo de elementos que va a hospedar el control en el **Cuadro de herramientas**.

    En el ejemplo siguiente se muestra el atributo `ProvideToolboxControl` y la definición de clase ajustada.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Prueba del control

 Para probar un control del **cuadro de herramientas** , pruébelo primero en el entorno de desarrollo y, a continuación, pruébelo en una aplicación compilada.

#### <a name="to-test-the-control"></a>Para probar el control

1. Presione **F5** para **iniciar la depuración**.

    Este comando compila el proyecto y abre una segunda instancia experimental de Visual Studio que tiene el control instalado.

2. En la instancia experimental de Visual Studio, cree un proyecto de **aplicación de Windows Forms** .

3. En **Explorador de soluciones**, haga doble clic en *Form1. CS* para abrirlo en el diseñador si aún no está abierto.

4. En el **cuadro de herramientas**, el `Counter` control debe mostrarse en la sección **General** .

5. Arrastre un `Counter` control al formulario y, a continuación, selecciónelo. Las `Value` `Message` propiedades, y se `ShowReset` mostrarán en la ventana **propiedades** , junto con las propiedades que se heredan de <xref:System.Windows.Forms.UserControl> .

6. Establezca la propiedad `Message` en `Count:`.

7. Arrastre un <xref:System.Windows.Forms.Button> control al formulario y, a continuación, establezca las propiedades de nombre y texto del botón en `Test` .

8. Haga doble clic en el botón para abrir *Form1. CS* en la vista de código y crear un controlador de clic.

9. En el controlador de clics, llame a `counter1.Increment()` .

10. En la función constructora, después de la llamada a `InitializeComponent` , escriba `counter1``.``Incremented +=` y, a continuación, presione la **tecla TAB** dos veces.

    Visual Studio genera un controlador de nivel de formulario para el `counter1.Incremented` evento.

11. Resalte la `Throw` instrucción en el controlador de eventos, escriba `mbox` y, a continuación, presione la **tecla TAB** dos veces para generar un cuadro de mensaje desde el fragmento de código mbox.

12. En la línea siguiente, agregue el siguiente `if` / `else` bloque para establecer la visibilidad del botón **restablecer** .

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Presione **F5**.

    Se abre el formulario. El `Counter` control muestra el texto siguiente.

    **Recuento: 0**

14. Seleccione **Probar**.

    El contador se incrementa y Visual Studio muestra un cuadro de mensaje.

15. Cierre el cuadro de mensaje.

    Desaparece el botón **restablecer** .

16. Seleccione **prueba** hasta que el contador llegue a **5** cerrando los cuadros de mensaje cada vez.

    Vuelve a aparecer el botón **restablecer** .

17. Seleccione **Restablecer**.

    El contador se restablece en **0**.

## <a name="next-steps"></a>Pasos siguientes

Al compilar un control de **cuadro de herramientas** , Visual Studio crea un archivo denominado *projectname. vsix* en la carpeta \bin\debug\ del proyecto. Puede implementar el control cargando el archivo *. vsix* en una red o en un sitio Web. Cuando un usuario abre el archivo *. vsix* , el control se instala y se agrega al cuadro de **herramientas** de Visual Studio en el equipo del usuario. Como alternativa, puede cargar el archivo *. vsix* en [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para que los usuarios puedan encontrarlo examinando el cuadro de diálogo **herramientas**  >  **extensiones y actualizaciones** .

## <a name="see-also"></a>Consulte también

- [Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Crear un control de cuadro de herramientas de WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Aspectos básicos del desarrollo de Windows Forms control](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
