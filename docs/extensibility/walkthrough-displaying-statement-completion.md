---
title: 'Tutorial: Mostrar la finalización de instrucciones | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e30c48e0d7c4c7c98b533555e1b4dac8888af7c5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710401"
---
# <a name="walkthrough-display-statement-completion"></a>Tutorial: Mostrar la finalización de instrucciones
Puede implementar la finalización de instrucciones en lenguaje mediante la definición de los identificadores para el que desea proporcionar finalización y, a continuación, desencadenar una sesión de finalización. Puede definir la finalización de instrucciones en el contexto de un servicio de lenguaje, definir su propia extensión de nombre de archivo y el tipo de contenido y, a continuación, Mostrar finalización para exclusivamente ese tipo. O bien, puede desencadenar la finalización de un tipo de contenido existente, por ejemplo, "texto simple". Este tutorial muestra cómo desencadenar la finalización de instrucciones para el tipo de contenido "texto simple", que es el tipo de contenido de archivos de texto. El tipo de contenido "text" es el antecesor de todos los otros tipos de contenido, incluidos archivos de código y XML.

 Normalmente se activa la finalización de instrucciones escribiendo algunos caracteres, por ejemplo, escribiendo el principio de un identificador como el "uso". Normalmente se cierra al presionar el **barra espaciadora**, **ficha**, o **ENTRAR** clave para confirmar una selección. Puede implementar las características de IntelliSense que se activan cuando se escribe un carácter mediante el uso de un controlador de comandos para las pulsaciones de teclas (el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz) y un proveedor del controlador que implementa el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de finalización, que es la lista de identificadores que participan en la finalización, implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaz y un proveedor de código fuente de finalización (el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfaz). Los proveedores son componentes de Managed Extensibility Framework (MEF). Que son responsables de las clases de origen y el controlador de exportación e importación de los servicios y los agentes, por ejemplo, el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, lo que permite la navegación en el búfer de texto y el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, lo que desencadena la sesión de finalización.

 Este tutorial muestra cómo implementar la finalización de instrucciones para un conjunto codificado de forma rígida de identificadores. En implementaciones completas, el servicio de lenguaje y la documentación del lenguaje son responsables de proporcionar ese contenido.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `CompletionTest`.

2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3.  Elimine los archivos de clase existentes.

4.  Agregue las siguientes referencias al proyecto y asegúrese de que **CopyLocal** está establecido en `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementar el origen de finalización
 El origen de finalización es responsable de recopilar el conjunto de identificadores y agrega el contenido a la ventana de finalización cuando un usuario escribe un desencadenador de finalización, como las primeras letras de un identificador. En este ejemplo, los identificadores y sus descripciones están codificados en el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método. En la mayoría de los usos reales, usaría el analizador de su lenguaje para obtener los tokens para rellenar la lista de finalización.

### <a name="to-implement-the-completion-source"></a>Para implementar el origen de finalización

1.  Agregue un archivo de clase y asígnele el nombre `TestCompletionSource`.

2.  Agregue estas importaciones:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3.  Modifique la declaración de clase para `TestCompletionSource` para que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4.  Agregar campos privados para el proveedor de origen, el búfer de texto y una lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos (que se corresponden con los identificadores que participarán en la sesión de finalización):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5.  Agregue un constructor que establece el búfer y el proveedor de código fuente. La `TestCompletionSourceProvider` clase se define en pasos posteriores:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método mediante la adición de un conjunto de finalizaciones que contiene las finalizaciones que desea proporcionar en el contexto. Cada conjunto de finalizaciones contiene un conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> finalizaciones y corresponde a una ficha de la ventana de finalización. (En proyectos de Visual Basic, las pestañas de la ventana de finalización se denominan **común** y **todas**.) El método `FindTokenSpanAtPosition` se define en el paso siguiente.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7.  El método siguiente se utiliza para buscar la palabra actual desde la posición del cursor:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8.  Implemente el `Dispose()` método:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementar el proveedor de origen de finalización
 El proveedor de origen de finalización es el elemento de componente MEF que crea una instancia del origen de finalización.

### <a name="to-implement-the-completion-source-provider"></a>Para implementar el proveedor de origen de finalización

1.  Agregue una clase denominada `TestCompletionSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportar a esta clase con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto sin formato" y un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "prueba de finalización".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2.  Importar un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que busca la palabra actual en el origen de finalización.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> método para crear una instancia del origen de finalización.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementar el proveedor de controlador de comandos de finalización
 El proveedor de controlador de comandos de finalización se deriva un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, que escucha un evento de creación de la vista de texto y convierte la vista de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, lo que permite la adición del comando a la cadena de comando del shell de Visual Studio: a un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Dado que esta clase es una exportación MEF, también puede usar para importar los servicios requeridos por el propio controlador de comandos.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar el proveedor de controlador de comandos de finalización

1.  Agregue un archivo denominado `TestCompletionCommandHandler`.

2.  Agregue las siguientes instrucciones using:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3.  Agregue una clase denominada `TestCompletionHandlerProvider` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportar a esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "controlador de finalización de token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto sin formato" y un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4.  Importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, que permite la conversión de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>y un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> que habilita el acceso a los servicios de Visual Studio estándar.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5.  Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método para crear una instancia del controlador de comandos.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementar el controlador de comandos de finalización
 Dado que se desencadena la finalización de instrucciones por pulsaciones de teclas, debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para recibir y procesar las pulsaciones de teclas que se desencadenen, confirmarán y descartar la sesión de finalización.

#### <a name="to-implement-the-completion-command-handler"></a>Para implementar el controlador de comandos de finalización

1. Agregue una clase denominada `TestCompletionCommandHandler` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Agregar campos privados para el siguiente controlador de comandos (al que pasar el comando), la vista de texto, el proveedor del controlador de comandos (que permite el acceso a diversos servicios) y una sesión de finalización:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Agregue un constructor que establece la vista de texto y los campos del proveedor y el comando se agrega a la cadena de comando:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método pasando el comando a lo largo de:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implemente el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Cuando este método recibe una pulsación de tecla, debe realizar una de estas cosas:

   - Permitir que el carácter que se escriben en el búfer y, a continuación, desencadenar o filtrar la finalización. (Caracteres imprimibles hacen esto).

   - Confirmar la finalización, pero no se permite el carácter que se va a escribir en el búfer. (Espacio en blanco, **ficha**, y **ENTRAR** hacerlo cuando se muestra una sesión de finalización.)

   - Permitir que el comando que pase al siguiente controlador de. (Todos los demás comandos.)

     Dado que este método puede mostrar la interfaz de usuario, llamar a <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> para asegurarse de que no se llama en un contexto de automatización:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Este código es un método privado que desencadena la sesión de finalización:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. El ejemplo siguiente es un método privado que cancela la suscripción desde el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> eventos:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución CompletionTest y ejecútelo en la instancia experimental.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar y probar la solución CompletionTest

1.  Compile la solución.

2.  Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3.  Cree un archivo de texto y escriba algún texto que incluye la palabra "Agregar".

4.  A medida que escribe primero "a" y, a continuación, "d", debe aparecer una lista que contiene "suma" y "adaptación". Tenga en cuenta que está seleccionada la suma. Cuando se escribe otra "d", la lista debe contener sólo "suma", que ahora está seleccionado. Puede confirmar "suma" presionando el **barra espaciadora**, **ficha**, o **ENTRAR** clave o descartar la lista escribiendo Esc o cualquier otra clave.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)