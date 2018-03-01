---
title: "Tutorial: Mostrar la finalización de instrucciones | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d9c3b44bd46c34a864896cbf1002505085be5143
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-statement-completion"></a>Tutorial: Mostrar la finalización de instrucciones
Puede implementar la finalización de instrucciones basada en lenguaje definiendo los identificadores para los que desea proporcionar finalización y, a continuación, desencadenar una sesión de finalización. Puede definir la finalización de instrucciones en el contexto de un servicio de lenguaje, defina su propia extensión de nombre de archivo y el tipo de contenido y, a continuación, mostrar la finalización de ese tipo, o puede desencadenar la finalización de un tipo de contenido existente, por ejemplo, "texto simple". Este tutorial muestra cómo desencadenar la finalización de instrucciones para el tipo de contenido "texto simple", que es el tipo de contenido de archivos de texto. El tipo de contenido "text" es el antecesor de todos los demás tipos de contenido, incluidos los archivos de código y XML.  
  
 Normalmente se desencadena la finalización de instrucciones para ello, escriba algunos caracteres, por ejemplo, para ello, escriba el principio de un identificador como "using". Normalmente se cierra al presionar la tecla BARRA ESPACIADORA, Tab o ENTRAR para confirmar una selección. Puede implementar las características de IntelliSense que se desencadenan al escribir un carácter con un controlador de comandos para las pulsaciones de teclas (el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz) y un proveedor de controlador que implementa el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de finalización, que es la lista de identificadores que participan en la finalización, implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaz y un proveedor de código fuente de finalización (el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfaz). Los proveedores son componentes de Managed Extensibility Framework (MEF). Son responsables de las clases de origen y el controlador de exportación e importación de servicios y los corredores de bolsa: por ejemplo, el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, lo que permite la navegación en el búfer de texto y el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, lo que desencadena la sesión de finalización.  
  
 Este tutorial muestra cómo implementar la finalización de instrucciones para un conjunto de identificadores codificados de forma rígida. En implementaciones completas, el servicio de lenguaje y la documentación para el idioma son responsables de proporcionar ese contenido.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Crear un proyecto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de C# VSIX. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Llame a la solución `CompletionTest`.  
  
2.  Agregar una plantilla de elementos de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
4.  Agregue las siguientes referencias al proyecto y asegúrese de que **CopyLocal** está establecido en `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementar el origen de finalización  
 El origen de finalización es responsable de recopilar el conjunto de identificadores y agregar el contenido a la ventana de finalización cuando un usuario escribe un desencadenador de finalización, como las primeras letras de un identificador. En este ejemplo, los identificadores y sus descripciones están codificados de forma rígida en el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método. En la mayoría de los usos de mundo real, utilizaría el analizador de su lenguaje para obtener los tokens para rellenar la lista de finalización.  
  
#### <a name="to-implement-the-completion-source"></a>Para implementar el origen de finalización  
  
1.  Agregue un archivo de clase y asígnele el nombre `TestCompletionSource`.  
  
2.  Agregue estas importaciones:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modifique la declaración de clase para `TestCompletionSource` para que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Agregue campos privados para el proveedor de origen, el búfer de texto y una lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos (que corresponden a los identificadores que vaya a participar en la sesión de finalización):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Agregue un constructor que establece el búfer y el proveedor de código fuente. La `TestCompletionSourceProvider` clase se define en pasos posteriores:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método mediante la adición de un conjunto de finalización que contiene las operaciones que desea proporcionar en el contexto. Cada conjunto de finalización contiene un conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> finalizaciones y corresponde a una ficha de la ventana de finalización. (En proyectos de Visual Basic, las fichas de la ventana de finalización se denominan **común** y **todas las**.) El método FindTokenSpanAtPosition se define en el paso siguiente.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  El método siguiente se utiliza para buscar la palabra actual desde la posición del cursor:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implemente el `Dispose()` método:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementar el proveedor de código fuente de finalización  
 El proveedor de código fuente de finalización es la parte del componente MEF que crea una instancia del origen de finalización.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Para implementar el proveedor de origen de finalización  
  
1.  Agregue una clase denominada `TestCompletionSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportar esta clase con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto simple" y un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "conclusión de prueba".  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importar un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que se usa para buscar la palabra actual en el origen de finalización.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> método para crear una instancia del origen de finalización.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementar el proveedor del controlador de comandos de finalización  
 El proveedor de controlador de comandos de finalización se deriva de un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, que realiza escuchas para un evento de creación de la vista de texto y convierte la vista de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, lo que permite la adición del comando a la cadena de comando del shell de Visual Studio: para una <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Dado que esta clase es una exportación MEF, también se puede usar para importar los servicios requeridos por el propio controlador de comandos.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar el proveedor de controlador de comandos de finalización  
  
1.  Agregue un archivo denominado `TestCompletionCommandHandler`.  
  
2.  Agregue estas instrucciones using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Agregue una clase denominada `TestCompletionHandlerProvider` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportar esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "controlador de finalización token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto simple" y un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, que permite la conversión de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>y un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> que permite el acceso a los servicios estándar de Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método para crear una instancia del controlador de comandos.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementar el controlador de comandos de finalización  
 Dado que la finalización de instrucciones se desencadena por pulsaciones de teclas, debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para recibir y procesar las pulsaciones de teclas que desencadenan, commit y descartar la sesión de finalización.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Para implementar el controlador de comandos de finalización  
  
1.  Agregue una clase denominada `TestCompletionCommandHandler` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Agregue campos privados para el siguiente controlador de comandos (al que pasar el comando), la vista de texto, el proveedor del controlador de comandos (que permite el acceso a diversos servicios) y una sesión de finalización:  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Agregue un constructor que establece la vista de texto y los campos de proveedor y agrega el comando a la cadena de comando:  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método pasando el comando a lo largo de:  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implemente el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Cuando este método recibe una pulsación de tecla, debe realizar una de estas acciones:  
  
    -   Permitir que el carácter que se escribe en el búfer y, a continuación, desencadenar o filtrar la finalización. (Caracteres imprimibles hacen esto).  
  
    -   Confirmar la finalización, pero no permiten el carácter que se va a escribirse en el búfer. (Espacio en blanco, ENTRAR y tabulador hacen esto cuando se muestra una sesión de finalización).  
  
    -   Permitir que el comando que se pasa al siguiente controlador. (Todos los demás comandos.)  
  
     Dado que este método puede mostrar la interfaz de usuario, llamar a <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> para asegurarse de que no se llama en un contexto de automatización:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Este código es un método privado que desencadena la sesión de finalización:  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  El ejemplo siguiente es un método privado que cancela la suscripción desde el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> eventos:  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución CompletionTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar y probar la solución CompletionTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba el texto que incluye la palabra "Agregar".  
  
4.  Mientras se escribe primero "a" y, a continuación, "d", debe mostrarse una lista que contiene "suma" y "adaptación". Tenga en cuenta que está seleccionada la suma. Cuando se escribe otra "d", la lista debe contener solo "suma", que se ha seleccionado. Puede confirmar "suma" presionando la tecla BARRA ESPACIADORA, Tab o Intro o descartar la lista escribiendo Esc o cualquier otra clave.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)