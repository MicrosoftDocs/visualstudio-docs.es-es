---
title: Creación de un control de cuadro de herramientas de formularios Windows Forms ? Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739585"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Crear un control de cuadro de herramientas de formularios Windows Forms

La plantilla de elemento Control de cuadro de herramientas de Windows Forms que se incluye en las herramientas de extensibilidad de Visual Studio (VS SDK), permite crear un control **de cuadro** de herramientas que se agrega automáticamente cuando se instala la extensión. En este tutorial se muestra cómo usar la plantilla para crear un control de contador simple que puede distribuir a otros usuarios.

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-the-toolbox-control"></a>Crear el control de cuadro de herramientas

La plantilla Control de cuadro de herramientas de formularios Windows Forms crea un control de usuario indefinido y proporciona toda la funcionalidad necesaria para agregar el control al **cuadro de herramientas.**

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Cree una extensión con un control de cuadro de herramientas de formularios Windows Forms

1. Cree un proyecto `MyWinFormsControl`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto,** buscando "vsix".

2. Cuando se abra el proyecto, agregue una `Counter`plantilla de elemento Control de cuadro de herramientas de Formularios Windows **Forms** denominada . En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento,** vaya a**Extensibilidad** de **Visual C-** > y seleccione Control de cuadro de herramientas de **formularios Windows Forms**

3. Esto agrega un control `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> de usuario, un para colocar el control en el cuadro de **herramientas**y un **Microsoft.VisualStudio.ToolboxControl** Asset entrada en el manifiesto VSIX para la implementación.

### <a name="build-a-user-interface-for-the-control"></a>Crear una interfaz de usuario para el control

El `Counter` control requiere dos controles <xref:System.Windows.Forms.Label> secundarios: a para <xref:System.Windows.Forms.Button> mostrar el recuento actual y a para restablecer el recuento a 0. No se requiere ningún otro control secundario porque los llamadores incrementarán el contador mediante programación.

#### <a name="to-build-the-user-interface"></a>Para crear la interfaz de usuario

1. En el **Explorador**de soluciones, haga doble clic en *Counter.cs* para abrirlo en el diseñador.

2. Retire el **haga clic aquí !** botón que se incluye de forma predeterminada al agregar la plantilla de elemento Control de cuadro de herramientas de Windows Forms.

3. Desde el **cuadro** `Label` de herramientas `Button` , arrastre un control y, a continuación, un control debajo de él a la superficie de diseño.

4. Cambie el tamaño del control de usuario general a 150, 50 píxeles y cambie el tamaño del control de botón a 50, 20 píxeles.

5. En la ventana **Propiedades,** establezca los siguientes valores para los controles de la superficie de diseño.

    |Control|Propiedad|Value|
    |-------------|--------------|-----------|
    |`Label1`|**Texto**|""|
    |`Button1`|**Nombre**|btnReset|
    |`Button1`|**Texto**|Reset|

### <a name="code-the-user-control"></a>Codificar el control de usuario

El `Counter` control expondrá un método para incrementar el contador, un evento que se generará siempre que se incremente el contador, un botón **Restablecer** y tres propiedades para almacenar el recuento actual, el texto para mostrar y si se va a mostrar u ocultar el botón **Restablecer.** El atributo `ProvideToolboxControl` determina la ubicación del **Cuadro de herramientas** donde se mostrará el control `Counter` .

#### <a name="to-code-the-user-control"></a>Para codificar el control de usuario

1. Haga doble clic en el formulario para abrir su controlador de eventos de carga en la ventana de código.

2. Por encima del método de controlador de eventos, en la clase de control cree un entero para almacenar el valor del contador y una cadena para almacenar el texto para mostrar como se muestra en el ejemplo siguiente.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Cree las siguientes declaraciones de propiedad pública.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Los llamadores pueden acceder a estas propiedades para obtener y establecer el texto de visualización del contador y para mostrar u ocultar el botón **Restablecer.** Los llamadores pueden obtener el `Value` valor actual de la propiedad de solo lectura, pero no pueden establecer el valor directamente.

4. Coloque el código `Load` siguiente en el evento para el control.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Establecer **Label** el texto <xref:System.Windows.Forms.UserControl.Load> Etiqueta en el evento permite que las propiedades de destino se carguen antes de aplicar sus valores. Establecer el texto **Label** en el constructor daría como resultado un **Label**vacío.

5. Cree el siguiente método público para incrementar el contador.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Agregue una declaración para el `Incremented` evento a la clase de control.

    ```csharp
    public event EventHandler Incremented;
    ```

    Los llamadores pueden agregar controladores a este evento para responder a los cambios en el valor del contador.

7. Vuelva a la vista de **Reset** diseño y `btnReset_Click` haga doble clic en el botón Restablecer para generar el controlador de eventos y, a continuación, rellénelo como se muestra en el ejemplo siguiente.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Justo encima de la definición de clase en la declaración de atributos de `ProvideToolboxControl` , cambie el valor del primer parámetro de `"MyWinFormsControl.Counter"` a `"General"`. Se establece el nombre del grupo de elementos que va a hospedar el control en el **Cuadro de herramientas**.

    En el ejemplo siguiente se muestra el atributo `ProvideToolboxControl` y la definición de clase ajustada.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Prueba del control

 Para probar un control **Toolbox,** pruébelo primero en el entorno de desarrollo y, a continuación, pruébelo en una aplicación compilada.

#### <a name="to-test-the-control"></a>Para probar el control

1. Presione **F5** para **iniciar la depuración**.

    Este comando compila el proyecto y abre una segunda instancia experimental de Visual Studio que tiene el control instalado.

2. En la instancia experimental de Visual Studio, cree un proyecto de aplicación de **Windows Forms.**

3. En el **Explorador**de soluciones , haga doble clic en *Form1.cs* para abrirlo en el diseñador si aún no está abierto.

4. En el cuadro `Counter` de **herramientas**, el control debe mostrarse en la sección **General.**

5. Arrastre `Counter` un control al formulario y, a continuación, selecciónelo. Las `Value` `Message`propiedades `ShowReset` , , y se mostrarán en la ventana **Propiedades,** junto con las propiedades heredadas de <xref:System.Windows.Forms.UserControl>.

6. Establezca la propiedad `Message` en `Count:`.

7. Arrastre <xref:System.Windows.Forms.Button> un control al formulario y, a continuación, establezca `Test`las propiedades de nombre y texto del botón en .

8. Haga doble clic en el botón para abrir *Form1.cs* en la vista de código y crear un controlador de clics.

9. En el controlador `counter1.Increment()`de clics, llame a .

10. En la función constructora, `counter1``.``Incremented +=` después de la llamada a , escriba y, a `InitializeComponent`continuación, presione **Tab** dos veces.

    Visual Studio genera un controlador `counter1.Incremented` de nivel de formulario para el evento.

11. Resalte `Throw` la instrucción en `mbox`el controlador de eventos, escriba y, a continuación, presione **Tab** dos veces para generar un cuadro de mensaje a partir del fragmento de código mbox.

12. En la siguiente línea, `if` / `else` agregue el siguiente bloque para establecer la visibilidad del botón **Restablecer.**

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Presione **F5**.

    Se abre el formulario. El `Counter` control muestra el texto siguiente.

    **Recuento: 0**

14. Haga clic en **Probar**.

    El contador aumenta y Visual Studio muestra un cuadro de mensaje.

15. Cierre el cuadro de mensaje.

    El botón **Restablecer** desaparece.

16. Haga clic en **Probar** hasta que el contador alcance **5** cerrando los cuadros de mensaje cada vez.

    El botón **Restablecer** vuelve a aparecer.

17. Haga clic en **Restablecer**.

    El contador se restablece a **0**.

## <a name="next-steps"></a>Pasos siguientes

Al compilar un control **de cuadro** de herramientas, Visual Studio crea un archivo denominado *ProjectName.vsix* en la carpeta . Puede implementar el control cargando el archivo *.vsix* en una red o en un sitio Web. Cuando un usuario abre el archivo *.vsix,* el control se instala y se agrega al cuadro de **herramientas** de Visual Studio en el equipo del usuario. Como alternativa, puede cargar el archivo *.vsix* en [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para que los usuarios puedan encontrarlo examinando en el cuadro de diálogo**Extensiones y actualizaciones** de **herramientas.** > 

## <a name="see-also"></a>Vea también

- [Ampliar otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Crear un control de cuadro de herramientas de WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Ampliar otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Los formularios Windows Forms controlan los conceptos básicos de desarrollo](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
