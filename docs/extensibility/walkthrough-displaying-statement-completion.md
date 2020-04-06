---
title: 'Tutorial: Visualización de la finalización de la instrucción ( Statement Completion) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697410"
---
# <a name="walkthrough-display-statement-completion"></a>Tutorial: Mostrar la finalización de instrucciones
Puede implementar la finalización de instrucciones basadas en lenguaje definiendo los identificadores para los que desea proporcionar la finalización y, a continuación, desencadenando una sesión de finalización. Puede definir la finalización de instrucciones en el contexto de un servicio de lenguaje, definir su propia extensión de nombre de archivo y tipo de contenido y, a continuación, mostrar la finalización solo para ese tipo. O bien, puede desencadenar la finalización de un tipo de contenido existente, por ejemplo, "texto sin formato". En este tutorial se muestra cómo desencadenar la finalización de instrucciones para el tipo de contenido "texto sin formato", que es el tipo de contenido de los archivos de texto. El tipo de contenido "texto" es el antepasado de todos los demás tipos de contenido, incluidos el código y los archivos XML.

 La finalización de instrucciones normalmente se desencadena escribiendo ciertos caracteres, por ejemplo, escribiendo el principio de un identificador como "using". Normalmente se descarta presionando la tecla **Barra espaciadora**, **Tabulador**o **Intro** para confirmar una selección. Puede implementar las características de IntelliSense que se desencadenan al escribir un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> carácter mediante un controlador <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> de comandos para las pulsaciones de teclas (la interfaz) y un proveedor de controlador que implementa la interfaz. Para crear el origen de finalización, que es la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> lista de identificadores que <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> participan en la finalización, implemente la interfaz y un proveedor de origen de finalización (la interfaz). Los proveedores son componentes de Managed Extensibility Framework (MEF). Son responsables de exportar las clases de origen y controlador e <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>importar servicios y intermediarios, por <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>ejemplo, el , que habilita la navegación en el búfer de texto y el , que desencadena la sesión de finalización.

 En este tutorial se muestra cómo implementar la finalización de instrucciones para un conjunto de identificadores codificado de forma rígida. En las implementaciones completas, el servicio de lenguaje y la documentación de idioma son responsables de proporcionar ese contenido.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `CompletionTest`nombre a la solución .

2. Agregue una plantilla de elemento Clasificador de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

4. Agregue las siguientes referencias al proyecto y asegúrese `false`de que **CopyLocal** está establecido en :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementar la fuente de finalización
 El origen de finalización es responsable de recopilar el conjunto de identificadores y agregar el contenido a la ventana de finalización cuando un usuario escribe un desencadenador de finalización, como las primeras letras de un identificador. En este ejemplo, los identificadores y sus descripciones <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> están codificados de forma rígida en el método. En la mayoría de los usos del mundo real, usaría el analizador de su idioma para obtener los tokens para rellenar la lista de finalización.

### <a name="to-implement-the-completion-source"></a>Para implementar la fuente de finalización

1. Agregue un archivo de clase y asígnele el nombre `TestCompletionSource`.

2. Agregue estas importaciones:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modifique la declaración de clase para `TestCompletionSource` que <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>implemente:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Agregue campos privados para el proveedor de origen, el búfer de texto y una lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos (que corresponden a los identificadores que participarán en la sesión de finalización):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Agregue un constructor que establezca el proveedor de origen y el búfer. La `TestCompletionSourceProvider` clase se define en pasos posteriores:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> el método agregando un conjunto de finalización que contenga las terminaciones que desea proporcionar en el contexto. Cada conjunto de finalización contiene un conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> terminaciones y corresponde a una pestaña de la ventana de finalización. (En los proyectos de Visual Basic, las pestañas de la ventana de finalización se denominan **Común** y **Todos**.) El `FindTokenSpanAtPosition` método se define en el paso siguiente.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. El siguiente método se utiliza para encontrar la palabra actual desde la posición del cursor:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implemente `Dispose()` el método:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementar el proveedor de origen de finalización
 El proveedor de origen de finalización es la parte del componente MEF que crea una instancia del origen de finalización.

### <a name="to-implement-the-completion-source-provider"></a>Para implementar el proveedor de origen de finalización

1. Agregue una `TestCompletionSourceProvider` clase denominada <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>que implemente . Exporte esta <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> clase con un "texto plano" y un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "finalización de prueba".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importar <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>un , que encuentra la palabra actual en el origen de finalización.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> el método para crear instancias del origen de finalización.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementar el proveedor de controlador de comandos de finalización
 El proveedor de controlador de <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>comandos de finalización se deriva de un , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>que escucha un evento de creación de vista de texto <xref:Microsoft.VisualStudio.Text.Editor.ITextView>y convierte la vista de un , que permite la adición del comando a la cadena de comandos del shell de Visual Studio, en un archivo . Dado que esta clase es una exportación MEF, también puede usarla para importar los servicios requeridos por el propio controlador de comandos.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar el proveedor de controlador de comandos de finalización

1. Agregue un `TestCompletionCommandHandler`archivo denominado .

2. Agregue estas directivas using:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Agregue una `TestCompletionHandlerProvider` clase denominada <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>que implemente . Exporte esta <xref:Microsoft.VisualStudio.Utilities.NameAttribute> clase con un de <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "controlador de finalización <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>token", un de "texto normal" y un de .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importe <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>el , que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> permite <xref:Microsoft.VisualStudio.Text.Editor.ITextView>la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>conversión <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> de a a , un , y un que permite el acceso a los servicios estándar de Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implemente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> el método para crear instancias del controlador de comandos.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementar el controlador de comandos de finalización
 Dado que la finalización de instrucciones se <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> desencadena mediante pulsaciones de teclas, debe implementar la interfaz para recibir y procesar las pulsaciones de teclas que desencadenan, confirman y descartan la sesión de finalización.

#### <a name="to-implement-the-completion-command-handler"></a>Para implementar el controlador de comandos de finalización

1. Agregue una `TestCompletionCommandHandler` clase denominada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>que implemente:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Agregue campos privados para el siguiente controlador de comandos (al que pasa el comando), la vista de texto, el proveedor de controlador de comandos (que permite el acceso a varios servicios) y una sesión de finalización:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Agregue un constructor que establezca la vista de texto y los campos del proveedor y agregue el comando a la cadena de comandos:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> el método pasando el comando a lo largo:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implemente el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Cuando este método recibe una pulsación de tecla, debe hacer una de estas cosas:

   - Permita que el carácter se escriba en el búfer y, a continuación, desencadene o filtre la finalización. (Los caracteres de impresión hacen esto.)

   - Confirme la finalización, pero no permita que el carácter se escriba en el búfer. (Espacio en blanco, **Tabulador**y **Entrar** hacen esto cuando se muestra una sesión de finalización.)

   - Permita que el comando se pase al siguiente controlador. (Todos los demás comandos.)

     Dado que este método <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> puede mostrar la interfaz de usuario, llame para asegurarse de que no se llama en un contexto de automatización:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Este código es un método privado que desencadena la sesión de finalización:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. El siguiente ejemplo es un método privado <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> que cancela las suscripciones del evento:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Compile y pruebe el código
 Para probar este código, compile la solución CompletionTest y ejecútela en la instancia experimental.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar y probar la solución CompletionTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba texto que incluya la palabra "añadir".

4. A medida que escribe primero "a" y luego "d", debe aparecer una lista que contenga "adición" y "adaptación". Observe que la adición está seleccionada. Cuando escribe otra "d", la lista debe contener solo "adición", que ahora está seleccionada. Puede confirmar "adición" pulsando la tecla **Barra espaciadora**, **Tabulador**o **Intro,** o descartar la lista escribiendo Esc o cualquier otra tecla.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
