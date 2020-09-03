---
title: 'Tutorial: Mostrar la finalización de instrucciones | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202012"
---
# <a name="walkthrough-displaying-statement-completion"></a>Tutorial: Visualización de finalización de instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar la finalización de instrucciones basada en el lenguaje si define los identificadores para los que desea proporcionar la finalización y, a continuación, desencadenar una sesión de finalización. Puede definir la finalización de instrucciones en el contexto de un servicio de lenguaje, definir su propia extensión de nombre de archivo y tipo de contenido y, a continuación, Mostrar la finalización solo para ese tipo, o puede desencadenar la finalización de un tipo de contenido existente, por ejemplo, "Plaintext". En este tutorial se muestra cómo desencadenar la finalización de instrucciones para el tipo de contenido "Plaintext", que es el tipo de contenido de los archivos de texto. El tipo de contenido "texto" es el antecesor de todos los demás tipos de contenido, incluidos los archivos de código y XML.  
  
 La finalización de instrucciones se desencadena normalmente escribiendo ciertos caracteres (por ejemplo, al escribir el principio de un identificador como "Using"). Normalmente se descarta presionando la barra espaciadora, la tabulación o la tecla entrar para confirmar una selección. Puede implementar las características de IntelliSense que se desencadenan escribiendo un carácter mediante un controlador de comandos para las pulsaciones de teclas (la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz) y un proveedor de controladores que implementa la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de finalización, que es la lista de identificadores que participan en la finalización, implemente la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaz y un proveedor de origen de finalización (la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfaz). Los proveedores son partes de componentes de Managed Extensibility Framework (MEF). Son responsables de exportar las clases de origen y de controlador e importar los servicios y los agentes, por ejemplo, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , que permite la navegación en el búfer de texto y <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , que desencadena la sesión de finalización.  
  
 En este tutorial se muestra cómo implementar la finalización de instrucciones para un conjunto de identificadores codificados de forma rígida. En las implementaciones completas, el servicio de lenguaje y la documentación del lenguaje son responsables de proporcionar ese contenido.  
  
## <a name="prerequisites"></a>Prerrequisitos  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Crear un proyecto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad**y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `CompletionTest` .  
  
2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Elimine los archivos de clase existentes.  
  
4. Agregue las siguientes referencias al proyecto y asegúrese de que **CopyLocal** está establecido en `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. Shell. immutable. 10.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-the-completion-source"></a>Implementar el origen de finalización  
 El origen de finalización es responsable de recopilar el conjunto de identificadores y de agregar el contenido a la ventana de finalización cuando un usuario escribe un desencadenador de finalización, como las primeras letras de un identificador. En este ejemplo, los identificadores y sus descripciones están codificados de forma rígida en el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método. En la mayoría de los usos del mundo real, se usaría el analizador del lenguaje para obtener los tokens para rellenar la lista de finalización.  
  
#### <a name="to-implement-the-completion-source"></a>Para implementar el origen de finalización  
  
1. Agregue un archivo de clase y asígnele el nombre `TestCompletionSource`.  
  
2. Agregue estas importaciones:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. Modifique la declaración de clase para para `TestCompletionSource` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. Agregue campos privados para el proveedor de origen, el búfer de texto y una lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos (que se corresponden con los identificadores que participarán en la sesión de finalización):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. Agregue un constructor que establezca el proveedor y el búfer de origen. La `TestCompletionSourceProvider` clase se define en pasos posteriores:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método agregando un conjunto de finalización que contenga las finalizaciones que desea proporcionar en el contexto. Cada conjunto de finalización contiene un conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> finalizaciones y corresponde a una pestaña de la ventana de finalización. (En proyectos de Visual Basic, las pestañas de la ventana de finalización se denominan **común** y **todos**). El método FindTokenSpanAtPosition se define en el paso siguiente.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. El método siguiente se usa para buscar la palabra actual desde la posición del cursor:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. Implemente el `Dispose()` método:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementar el proveedor de origen de finalización  
 El proveedor de origen de finalización es la parte del componente de MEF que crea una instancia del origen de finalización.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Para implementar el proveedor de origen de finalización  
  
1. Agregue una clase denominada `TestCompletionSourceProvider` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Exporte esta clase con <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Plaintext" y un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "finalización de prueba".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. Importe un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , que se usa para buscar la palabra actual en el origen de finalización.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> método para crear una instancia del origen de finalización.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementar el proveedor de controladores de comandos de finalización  
 El proveedor del controlador de comandos de finalización se deriva de un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , que escucha un evento de creación de la vista de texto y convierte la vista de, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> que permite agregar el comando a la cadena de comandos de Visual Studio Shell, a <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Dado que esta clase es una exportación de MEF, también puede usarla para importar los servicios que requiere el propio controlador de comandos.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar el proveedor del controlador de comandos de finalización  
  
1. Agregue un archivo denominado `TestCompletionCommandHandler` .  
  
2. Agregue estas instrucciones Using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. Agregue una clase denominada `TestCompletionHandlerProvider` que implemente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Exporte esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "controlador de finalización de token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Plaintext" y un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. Importe <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , que permite la conversión de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a,, <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> y a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> que permite el acceso a los servicios estándar de Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método para crear una instancia del controlador de comandos.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementar el controlador de comandos de finalización  
 Como la finalización de instrucciones se desencadena mediante pulsaciones de teclas, debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para recibir y procesar las pulsaciones de teclas que desencadenan, confirman y descartan la sesión de finalización.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Para implementar el controlador de comandos de finalización  
  
1. Agregue una clase denominada `TestCompletionCommandHandler` que implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Agregue campos privados para el siguiente controlador de comandos (al que se pasa el comando), la vista de texto, el proveedor del controlador de comandos (que permite el acceso a varios servicios) y una sesión de finalización:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Agregue un constructor que establezca la vista de texto y los campos de proveedor, y agregue el comando a la cadena de comandos:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método pasando el comando a lo largo de:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implemente el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Cuando este método recibe una pulsación de tecla, debe realizar una de estas acciones:  
  
   - Permita que el carácter se escriba en el búfer y, a continuación, desencadene o filtre la finalización. (Los caracteres de impresión lo hacen).  
  
   - Confirma la finalización, pero no permite que el carácter se escriba en el búfer. (Espacio en blanco, pestaña y escriba haga esto cuando se muestre una sesión de finalización).  
  
   - Permite pasar el comando al siguiente controlador. (El resto de comandos).  
  
     Dado que este método puede mostrar la interfaz de usuario, llame <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> a para asegurarse de que no se llama en un contexto de automatización:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Este código es un método privado que desencadena la sesión de finalización:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. El ejemplo siguiente es un método privado que cancela la suscripción del <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución CompletionTest y ejecútela en la instancia experimental.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar y probar la solución CompletionTest  
  
1. Compile la solución.  
  
2. Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3. Cree un archivo de texto y escriba algún texto que incluya la palabra "agregar".  
  
4. A medida que escribe primero "a" y luego "d", se debe mostrar una lista que contenga "suma" y "adaptación". Observe que está seleccionada la opción adición. Cuando escribe otra "d", la lista solo debe contener "suma", que ahora está seleccionada. Puede confirmar "suma" presionando la barra espaciadora, la tabulación o la tecla entrar, o bien descartar la lista escribiendo ESC o cualquier otra tecla.  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
