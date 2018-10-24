---
title: Creación de un editor de cuerpo HTTP personalizado para el Editor de pruebas de rendimiento web en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 338aade9ddef3c4ef571ea2a5bffc67064c81869
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862468"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Creación de un editor de cuerpo HTTP personalizado para el Editor de pruebas de rendimiento web

Puede crear un editor de contenido personalizado que le permita editar el contenido del texto de la cadena o del cuerpo binario de una solicitud de servicio web; por ejemplo, SOAP, REST, asmx, wcf, RIA y otros tipos de solicitudes de servicio web.

 Puede implementar estos tipos de editores:

-   **Editor de contenido de cadena** Se implementa usando la interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>.

-   **Editor de contenido binario** Se implementa usando la interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

Estas interfaces están contenidas en el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

## <a name="create-a-windows-control-library-project"></a>Crear un proyecto de Biblioteca de controles de Windows

### <a name="create-a-user-control-by-using-a-windows-control-library-project"></a>Crear un control de usuario mediante un proyecto de Biblioteca de controles de Windows

1. En el menú **Archivo** de Visual Studio, seleccione **Nuevo** y, después, seleccione **Proyecto**.

    Aparecerá el cuadro de diálogo **Nuevo proyecto**.

2. En **Plantillas instaladas**, seleccione **Visual Basic** o **Visual C#** dependiendo de su preferencia de programación y, después, seleccione **Windows**.

   > [!NOTE]
   > En este ejemplo se usa Visual C#.

3. En la lista de plantillas, seleccione **Biblioteca de controles de Windows Forms**.

4. En el cuadro de texto **Nombre**, escriba un nombre (por ejemplo, `MessageEditors`) y elija **Aceptar**.

   > [!NOTE]
   > En este ejemplo se usa MessageEditors.

    El proyecto se agregará a la nueva solución y aparecerá un <xref:System.Windows.Forms.UserControl> denominado *UserControl1.cs* en el diseñador.

5. En el **Cuadro de herramientas**, bajo la categoría **Controles comunes**, arrastre un <xref:System.Windows.Forms.RichTextBox> hasta la superficie de UserControl1.

6. Elija el glifo de la etiqueta de acción (![Glifo de etiqueta inteligente](../test/media/vs_winformsmttagglyph.gif)) situado en la esquina superior derecha del control <xref:System.Windows.Forms.RichTextBox> y seleccione **Acoplar en contenedor primario**.

7. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto Biblioteca de controles de Windows Forms y seleccione **Propiedades**.

8. En **Propiedades**, seleccione la pestaña **Aplicación**.

9. En la lista desplegable **Plataforma de destino**, seleccione **.NET Framework 4**.

10. Aparecerá el cuadro de diálogo **Cambio de plataforma de destino**.

11. Elija **Sí**.

12. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Referencias** y seleccione **Agregar referencia**.

13. Aparecerá el cuadro de diálogo **Agregar referencia**.

14. Elija la pestaña .**NET**, desplácese hacia abajo, seleccione **Microsoft.VisualStudio.QualityTools.WebTestFramework** y, luego, elija **Aceptar**.

15. Si el **Diseñador de vistas** todavía no está abierto, en el **Explorador de soluciones**, haga clic con el botón derecho en **UserControl1.cs** y, luego, seleccione **Diseñador de vistas**.

16. En la superficie de diseño, haga clic con el botón derecho y seleccione **Ver código**.

17. (Opcional) Cambie el nombre de la clase y el constructor de UserControl1 a un nombre significativo, por ejemplo MessageEditorControl:

    > [!NOTE]
    > En el ejemplo se usa MessageEditorControl.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

18. Agregue las siguientes propiedades para habilitar la obtención y el establecimiento del texto en RichTextBox1. La interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> usará EditString y <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> usará EditByteArray:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Agregar una clase para el proyecto Biblioteca de controles de Windows Forms

Agregue una clase al proyecto. Se usará para implementar las interfaces <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> y <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Información general del código de este procedimiento**

Se crea una instancia del <xref:System.Windows.Forms.UserControl> MessageEditorControl creado en el procedimiento anterior como messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

 La instancia de messageEditorControl se hospeda dentro del cuadro de diálogo de complemento creado por el método <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*>. Además, el <xref:System.Windows.Forms.RichTextBox> de messageEditorControl se rellena con el contenido de <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Sin embargo, la creación del complemento no se puede producir a menos que <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> devuelva `true`. En el caso de este editor, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> devuelve `true` si <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> en <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> contiene "xml".

 Cuando se completa la edición del texto de la cadena y el usuario hace clic en **Aceptar** en el cuadro de diálogo del complemento, se llama a <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> para obtener el texto editado como una cadena y actualizar el **Texto de la cadena** de la solicitud en el Editor de pruebas de rendimiento web.

### <a name="to-create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface-code"></a>Para crear una clase e implementar el código de la interfaz IStringHttpBodyEditorPlugin

1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto Biblioteca de controles de Windows Forms y seleccione **Agregar nuevo elemento**.

2.  Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

3.  Seleccione **Clase**.

4.  En el cuadro de texto **Nombre**, escriba un nombre significativo para la clase, por ejemplo, `MessageEditorPlugins`.

5.  Haga clic en **Agregar**.

     Class1 se agregará al proyecto y se presentará en el Editor de código.

6.  En el Editor de código, agregue la siguiente instrucción using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

7.  Escriba o copie el siguiente código para crear una instancia de la clase XmlMessageEditor de la interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> e implementar los métodos necesarios:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Agregar IBinaryHttpBodyEditorPlugin a la clase

Implementar la interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Información general del código de este procedimiento**

La implementación del código para la interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> es similar a la <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> tratada en el procedimiento anterior. Sin embargo, la versión binaria usa una matriz de bytes para administrar los datos binarios en lugar de una cadena.

Se crea una instancia del <xref:System.Windows.Forms.UserControl> MessageEditorControl creado en el primer procedimiento como messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

La instancia de messageEditorControl se hospeda dentro del cuadro de diálogo de complemento creado por el método <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*>. Además, el <xref:System.Windows.Forms.RichTextBox> de messageEditorControl se rellena con el contenido de <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Sin embargo, la creación del complemento no se puede producir a menos que <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> devuelva `true`. En el caso de este editor, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> devuelve `true` si <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> en <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> contiene "msbin1".

Cuando se completa la edición del texto de la cadena y el usuario hace clic en **Aceptar** en el cuadro de diálogo del complemento, se llama a <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> para obtener el texto editado como una cadena y actualizar **BinaryHttpBody.Data** de la solicitud en el Editor de pruebas de rendimiento web.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Para agregar IBinaryHttpBodyEditorPlugin a la clase

-   Escriba o copie el siguiente código bajo la clase XmlMessageEditor agregada en el procedimiento anterior para crear una instancia de la clase Msbin1MessageEditor de la interfaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> e implementar los métodos necesarios:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes.  This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Compilar e implementar los complementos

### <a name="to-build-and-deploy-the-resulting-dll-for-the-istringhttpbodyeditorplugin-and-ibinaryhttpbodyeditorplugin"></a>Para compilar e implementar el archivo dll resultante para IStringHttpBodyEditorPlugin e IBinaryHttpBodyEditorPlugin

1.  En el menú **Compilar**, elija **Compilar \<nombre del proyecto Biblioteca de control de Windows Forms**.

2.  Cierre todas las instancias de Visual Studio.

    > [!NOTE]
    > Al cerrarse Visual Studio, se garantiza que el archivo *.dll* no esté bloqueado antes de intentar copiarlo.

3.  Copie el archivo *.dll* resultante de la carpeta *bin\debug* del proyecto (por ejemplo, *MessageEditors.dll*) en *%ProgramFiles%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4.  Abra Visual Studio.

     Ahora, el archivo *.dll* está registrado con Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Comprobar los complementos usando una prueba de rendimiento web

### <a name="to-test-your-plug-ins"></a>Para probar los complementos

1.  Cree un proyecto de prueba.

2.  Cree una prueba de rendimiento web y escriba una dirección URL en el explorador a un servicio web.

3.  Al finalizar la grabación, en el Editor de pruebas de rendimiento web, expanda la solicitud para el servicio Web y seleccione **Texto de la cadena** o **Cuerpo binario**.

4.  En la ventana Propiedades, seleccione Texto de la cadena o Cuerpo binario y elija los puntos suspensivos **(...)**.

     Aparecerá el cuadro de diálogo **Editar datos del cuerpo HTTP**.

5.  Ahora, puede editar los datos y elegir **Aceptar**. Esto invoca el método GetNewValue aplicable para actualizar el contenido de <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Compilar el código

Compruebe que la versión de .NET Framework de destino para el proyecto Biblioteca de controles de Windows Forms sea .NET Framework 4.5. De forma predeterminada, los proyectos Biblioteca de controles de Windows Forms tienen como destino el marco de cliente .NET Framework 4.5, que no permitirá la inclusión de la referencia de Microsoft.VisualStudio.QualityTools.WebTestFramework.

Para más información, vea [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Cómo: Crear un complemento de nivel de solicitud](../test/how-to-create-a-request-level-plug-in.md)
- [Codificación de una regla de extracción personalizada para una prueba de rendimiento web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codificación de una regla de validación personalizada para una prueba de rendimiento web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Cómo: Crear un complemento de pruebas de carga](../test/how-to-create-a-load-test-plug-in.md)
- [Generar y ejecutar una prueba de rendimiento web codificada](../test/generate-and-run-a-coded-web-performance-test.md)
- [Cómo: Crear un complemento de Visual Studio para el visor de resultados de pruebas de rendimiento web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)