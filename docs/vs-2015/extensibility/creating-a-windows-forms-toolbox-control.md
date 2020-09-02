---
title: Crear un control Windows Forms Toolbox | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03fcc73c58baa1482c53e104a9946ffaa354f1a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698963"
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Creación de un control de cuadro de herramientas de Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La plantilla de elemento de control de cuadro de herramientas Windows Forms que se incluye en el Herramientas de extensibilidad de Visual Studio (SDK de VS) le permite crear un control que se agrega automáticamente al **cuadro de herramientas** cuando se instala la extensión. En este tema se muestra cómo usar la plantilla para crear un control de contador simple que se puede distribuir a otros usuarios.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Creación de un control de cuadro de herramientas de Windows Forms  
 La plantilla de control de cuadro de herramientas de Windows Forms crea un control de usuario no definido y proporciona todas las funciones necesarias para agregar el control al **cuadro de herramientas**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Crear una extensión con un control de cuadro de herramientas Windows Forms  
  
1. Cree un proyecto VSIX denominado `MyWinFormsControl` . Puede encontrar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** en **Visual C#/extensibilidad**.  
  
2. Cuando se abra el proyecto, agregue una plantilla de elemento de **control de cuadro de herramientas Windows Forms** denominada `Counter` . En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar o nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a **Visual C#/extensibilidad** y seleccione **Windows Forms control de cuadro de herramientas** .  
  
3. Esto agrega un control de usuario, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> para colocar el control en el **cuadro de herramientas**y una entrada de recurso **Microsoft. VisualStudio. TOOLBOXCONTROL** en el manifiesto de VSIX para la implementación.  
  
### <a name="building-a-user-interface-for-the-control"></a>Crear una interfaz de usuario para el control  
 El `Counter` control requiere dos controles secundarios: un <xref:System.Windows.Forms.Label> para mostrar el recuento actual y un <xref:System.Windows.Forms.Button> para restablecer el recuento en 0. No se requieren otros controles secundarios, ya que los llamadores incrementarán el contador mediante programación.  
  
##### <a name="to-build-the-user-interface"></a>Para crear la interfaz de usuario  
  
1. En **Explorador de soluciones**, haga doble clic en Counter.CS para abrirlo en el diseñador.  
  
2. Quite el vínculo "haga clic aquí". **Que se** incluye de forma predeterminada al agregar la plantilla de elemento de control de cuadro de herramientas Windows Forms.  
  
3. En el **cuadro de herramientas**, arrastre un `Label` control y, a continuación, un `Button` control situado debajo de él a la superficie de diseño.  
  
4. Cambie el tamaño del control de usuario general a 150, 50 píxeles, y cambie el tamaño del control de botón a 50, 20 píxeles.  
  
5. En la ventana **propiedades** , establezca los siguientes valores para los controles en la superficie de diseño.  
  
    |Control|Propiedad|Value|  
    |-------------|--------------|-----------|  
    |`Label1`|**Texto**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**Texto**|Reset|  
  
### <a name="coding-the-user-control"></a>Codificar el control de usuario  
 El control `Counter` presentará un método para incrementar el contador, un evento que se desencadenará cuando el contador se incremente, un botón `Reset` y tres propiedades para almacenar el recuento actual, el texto para mostrar y si se debe mostrar u ocultar el botón `Reset` . El atributo `ProvideToolboxControl` determina la ubicación del **Cuadro de herramientas** donde se mostrará el control `Counter` .  
  
##### <a name="to-code-the-user-control"></a>Para codificar el control de usuario  
  
1. Haga doble clic en el formulario para abrir el controlador de eventos de carga en la ventana de código.  
  
2. Encima del método de controlador de eventos, en la clase control, cree un entero para almacenar el valor del contador y una cadena para almacenar el texto para mostrar como se muestra en el ejemplo siguiente.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3. Cree las siguientes declaraciones de propiedades públicas.  
  
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
  
     Los llamadores pueden tener acceso a estas propiedades para obtener y establecer el texto para mostrar del contador y para mostrar u ocultar el `Reset` botón. Los llamadores pueden obtener el valor actual de la propiedad de solo lectura `Value` , pero no pueden establecer el valor directamente.  
  
4. Coloque el código siguiente en el `Load` evento para el control.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Establecer el texto de la **etiqueta** en el <xref:System.Windows.Forms.UserControl.Load> evento permite que se carguen las propiedades de destino antes de que se apliquen sus valores. Establecer el texto de la **etiqueta** en el constructor daría como resultado una **etiqueta**vacía.  
  
5. Cree el siguiente método público para incrementar el contador.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6. Agregue una declaración para el `Incremented` evento a la clase del control.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     Los llamadores pueden agregar controladores a este evento para responder a los cambios en el valor del contador.  
  
7. Vuelva a la vista de diseño y haga doble clic en el `Reset` botón para generar el `btnReset_Click` controlador de eventos y, a continuación, rellénelo como se muestra en el ejemplo siguiente.  
  
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
  
### <a name="testing-the-control"></a>Probar el control  
 Para probar un control del **cuadro de herramientas** , pruébelo primero en el entorno de desarrollo y, a continuación, pruébelo en una aplicación compilada.  
  
##### <a name="to-test-the-control"></a>Para probar el control  
  
1. Presione F5.  
  
     De este modo se compila el proyecto y se abre una segunda instancia experimental de Visual Studio que tiene el control instalado.  
  
2. En la instancia experimental de Visual Studio, cree un proyecto de **aplicación de Windows Forms** .  
  
3. En **Explorador de soluciones**, haga doble clic en Form1.CS para abrirlo en el diseñador si aún no está abierto.  
  
4. En el **cuadro de herramientas**, el `Counter` control debe mostrarse en la sección **General** .  
  
5. Arrastre un `Counter` control al formulario y, a continuación, selecciónelo. Las `Value` `Message` propiedades, y se `ShowReset` mostrarán en la ventana **propiedades** , junto con las propiedades que se heredan de <xref:System.Windows.Forms.UserControl> .  
  
6. Establezca la propiedad `Message` en `Count:`.  
  
7. Arrastre un <xref:System.Windows.Forms.Button> control al formulario y, a continuación, establezca las propiedades de nombre y texto del botón en `Test` .  
  
8. Haga doble clic en el botón para abrir Form1.cs en la vista de código y crear un controlador de clic.  
  
9. En el controlador de clics, llame a `counter1.Increment()` .  
  
10. En la función constructora, después de la llamada a `InitializeComponent` , escriba `counter1``.``Incremented +=` y, a continuación, presione la tecla TAB dos veces.  
  
     Visual Studio genera un controlador de nivel de formulario para el `counter1.Incremented` evento.  
  
11. Resalte la `Throw` instrucción en el controlador de eventos, escriba `mbox` y, a continuación, presione la tecla TAB dos veces para generar un cuadro de mensaje desde el fragmento de código mbox.  
  
12. En la línea siguiente, agregue el siguiente `if` / `else` bloque para establecer la visibilidad del `Reset` botón.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Presione F5.  
  
     Se abre el formulario. El `Counter` control muestra el texto siguiente.  
  
     **Recuento: 0**  
  
14. Haga clic en **Probar**.  
  
     El contador se incrementa y Visual Studio muestra un cuadro de mensaje.  
  
15. Cierre el cuadro de mensaje.  
  
     Desaparece el botón **restablecer** .  
  
16. Haga clic en **probar** hasta que el contador llegue a **5** cerrando los cuadros de mensaje cada vez.  
  
     Vuelve a aparecer el botón **restablecer** .  
  
17. Haga clic en **Restablecer**.  
  
     El contador se restablece en **0**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Cuando se crea un control del **Cuadro de herramientas** , Visual Studio crea un archivo denominado *NombreDelProyecto*.vsix en la carpeta \bin\debug\ del proyecto. Para implementar el control, puede cargar el archivo .vsix en una red o un sitio web. Cuando un usuario abre el archivo. vsix, el control se instala y se agrega al cuadro de **herramientas** de Visual Studio en el equipo del usuario. Como alternativa, puede cargar el archivo. vsix en el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para que los usuarios puedan encontrarlo examinando el cuadro de diálogo **herramientas/extensión y actualizaciones** .  
  
## <a name="see-also"></a>Consulte también  
 [Extender el cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Crear un control de cuadro de herramientas de WPF](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Fundamentos de desarrollo de controles de formularios Windows Forms](https://msdn.microsoft.com/library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)
