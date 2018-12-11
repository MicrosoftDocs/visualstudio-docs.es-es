---
title: Crear un Windows Forms Control Toolbox | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 371fd4269cee5918bd0d0b623eb49e1f709a311d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781717"
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Creación de un control de cuadro de herramientas de Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La plantilla de elemento de Control de cuadro de herramientas de Windows Forms que se incluye en las herramientas de extensibilidad de Visual Studio (SDK de VS) le permite crear un control que se agrega automáticamente a la **cuadro de herramientas** cuando se instala la extensión. En este tema se muestra cómo usar la plantilla para crear un control de contador sencillo que puede distribuir a otros usuarios.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Creación de un control de cuadro de herramientas de Windows Forms  
 La plantilla de Control de cuadro de herramientas de Windows Forms crea un control de usuario no definido y proporciona toda la funcionalidad que es necesario para agregar el control a la **cuadro de herramientas**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Crear una extensión con un Control de cuadro de herramientas de Windows Forms  
  
1.  Cree un proyecto VSIX denominado `MyWinFormsControl`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Cuando se abra el proyecto, agregue un **Control Toolbox de Windows Forms** plantilla de elemento denominado `Counter`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **Control Toolbox de Windows Forms**  
  
3.  Esto agrega un control de usuario, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> para colocar el control en el **cuadro de herramientas**y un **Microsoft.VisualStudio.ToolboxControl** entrada del activo en el manifiesto VSIX para la implementación.  
  
### <a name="building-a-user-interface-for-the-control"></a>Crear una interfaz de usuario para el control  
 El `Counter` control requiere dos controles secundarios: una <xref:System.Windows.Forms.Label> para mostrar el recuento actual y un <xref:System.Windows.Forms.Button> para restablecer el recuento a 0. No hay más controles secundarios son necesarios porque los autores de llamadas incrementarán el contador mediante programación.  
  
##### <a name="to-build-the-user-interface"></a>Para crear la interfaz de usuario  
  
1.  En **el Explorador de soluciones**, haga doble clic en Counter.cs para abrirlo en el diseñador.  
  
2.  Quitar el "haga clic aquí!" **Botón** que se incluye de forma predeterminada cuando se agrega la plantilla de elemento de Control de cuadro de herramientas de Windows Forms.  
  
3.  Desde el **cuadro de herramientas**, arrastre un `Label` control y, a continuación, un `Button` control debajo de él en la superficie de diseño.  
  
4.  El tamaño del control de usuario general a 150, 50 píxeles y el botón de cambio de tamaño el control a 50, 20 píxeles.  
  
5.  En el **propiedades** ventana, establezca los siguientes valores para los controles en la superficie de diseño.  
  
    |Control|Propiedad|Valor|  
    |-------------|--------------|-----------|  
    |`Label1`|**Texto**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**Texto**|Restablecer|  
  
### <a name="coding-the-user-control"></a>Codificar el control de usuario  
 El control `Counter` presentará un método para incrementar el contador, un evento que se desencadenará cuando el contador se incremente, un botón `Reset` y tres propiedades para almacenar el recuento actual, el texto para mostrar y si se debe mostrar u ocultar el botón `Reset` . El atributo `ProvideToolboxControl` determina la ubicación del **Cuadro de herramientas** donde se mostrará el control `Counter` .  
  
##### <a name="to-code-the-user-control"></a>Para codificar el control de usuario  
  
1.  Haga doble clic en el formulario para abrir su controlador de eventos de carga en la ventana de código.  
  
2.  Por encima del método de controlador de eventos, en la clase del control crear un número entero para almacenar el valor del contador y una cadena para almacenar el texto para mostrar, como se muestra en el ejemplo siguiente.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Cree las siguientes declaraciones de propiedad pública.  
  
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
  
     Los autores de llamadas pueden tener acceso a estas propiedades para obtener y establecer el texto para mostrar del contador y para mostrar u ocultar el `Reset` botón. Los autores de llamadas pueden obtener el valor actual de solo lectura `Value` propiedad, pero no se puede establecer el valor directamente.  
  
4.  Coloque el siguiente código el `Load` eventos para el control.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Establecer el **etiqueta** texto en el <xref:System.Windows.Forms.UserControl.Load> evento permite cargar antes de que sus valores se aplican las propiedades de destino. Establecer el **etiqueta** texto en el constructor daría como resultado un valor vacío **etiqueta**.  
  
5.  Cree el siguiente método público para incrementar el contador.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Agregue una declaración para el `Incremented` eventos a la clase de control.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     Los autores de llamadas pueden agregar controladores a este evento para responder a cambios en el valor del contador.  
  
7.  Vuelva a la vista Diseño y haga doble clic en el `Reset` botón para generar el `btnReset_Click` controlador de eventos y, a continuación, rellene en como se muestra en el ejemplo siguiente.  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Justo encima de la definición de clase en la declaración de atributos de `ProvideToolboxControl` , cambie el valor del primer parámetro de `"MyWinFormsControl.Counter"` a `"General"`. Se establece el nombre del grupo de elementos que va a hospedar el control en el **Cuadro de herramientas**.  
  
     En el ejemplo siguiente se muestra el atributo `ProvideToolboxControl` y la definición de clase ajustada.  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>Probar el control  
 Para probar un **cuadro de herramientas** controlar, pruébelo primero en el entorno de desarrollo y, a continuación, vuelva a probarlo en una aplicación compilada.  
  
##### <a name="to-test-the-control"></a>Para probar el control  
  
1.  Presione F5.  
  
     Esto compila el proyecto y abre una segunda instancia Experimental de Visual Studio que tiene instalado el control.  
  
2.  En la instancia Experimental de Visual Studio, cree un **aplicación de Windows Forms** proyecto.  
  
3.  En **el Explorador de soluciones**, haga doble clic en Form1.cs para abrirlo en el diseñador si no está ya abierto.  
  
4.  En el **cuadro de herramientas**, `Counter` control debe mostrarse en el **General** sección.  
  
5.  Arrastre un `Counter` control al formulario y, a continuación, selecciónelo. El `Value`, `Message`, y `ShowReset` propiedades se mostrarán en el **propiedades** ventana, junto con las propiedades que se heredan de <xref:System.Windows.Forms.UserControl>.  
  
6.  Establezca la propiedad `Message` en `Count:`.  
  
7.  Arrastre un <xref:System.Windows.Forms.Button> control al formulario y, a continuación, establezca las propiedades de nombre y el texto del botón en `Test`.  
  
8.  Haga doble clic en el botón para abrir Form1.cs en la vista de código y crear un controlador de clic.  
  
9. En el controlador de clics, llame a `counter1.Increment()`.  
  
10. En la función constructora, después de llamar a `InitializeComponent`, tipo `counter1``.``Incremented +=` y, a continuación, presione TAB dos veces.  
  
     Visual Studio genera un controlador de nivel de formulario para el `counter1.Incremented` eventos.  
  
11. Resalte la `Throw` instrucción en el controlador de eventos, tipo `mbox`, y, a continuación, presione la tecla TAB dos veces para generar un cuadro de mensaje del fragmento de código de buzón.  
  
12. En la línea siguiente, agregue el siguiente `if` / `else` bloque para establecer la visibilidad de la `Reset` botón.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Presione F5.  
  
     Abre el formulario. El `Counter` control muestra el texto siguiente.  
  
     **Recuento: 0**  
  
14. Haga clic en **Probar**.  
  
     Los incrementos de contador y Visual Studio muestra un cuadro de mensaje.  
  
15. Cierre el cuadro de mensaje.  
  
     El **restablecer** botón desaparece.  
  
16. Haga clic en **prueba** hasta que el contador llega a **5** al cerrar el mensaje cuadros cada vez.  
  
     El **restablecer** botón vuelve a aparecer.  
  
17. Haga clic en **Restablecer**.  
  
     El contador se restablece a **0**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Cuando se crea un control del **Cuadro de herramientas** , Visual Studio crea un archivo denominado *NombreDelProyecto*.vsix en la carpeta \bin\debug\ del proyecto. Para implementar el control, puede cargar el archivo .vsix en una red o un sitio web. Cuando un usuario abre el archivo .vsix, el control está instalado y se agrega a la de Visual Studio **cuadro de herramientas** en el equipo del usuario. Como alternativa, puede cargar el archivo .vsix en el [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) del sitio Web para que los usuarios pueden buscarlo en el **herramientas / extensiones y actualizaciones** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Ampliar el cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Crear un Control de cuadro de herramientas WPF](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Fundamentos de desarrollo de controles de Windows Forms](http://msdn.microsoft.com/library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)

