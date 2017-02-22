---
title: "Tutorial: Mostrar la finalizaci&#243;n de instrucciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] nuevos - finalización de instrucciones"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
caps.handback.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
---
# Tutorial: Mostrar la finalizaci&#243;n de instrucciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede implementar la finalización de instrucciones basadas en lenguaje definiendo los identificadores para los que desea proporcionar finalización y, a continuación, desencadenar una sesión de finalización. Puede definir la finalización de instrucciones en el contexto de un servicio de lenguaje, definir su propia extensión de nombre de archivo y el tipo de contenido y, a continuación, Mostrar finalización de ese tipo o puede desencadenar la finalización de un tipo de contenido existente, por ejemplo, "texto simple". Este tutorial muestra cómo desencadenar la finalización de instrucciones para el tipo de contenido de "texto simple", que es el tipo de contenido de archivos de texto. El tipo de contenido "text" es el antecesor de todos los demás tipos de contenido, incluidos los archivos de código y XML.  
  
 Normalmente se activa la finalización de instrucciones escribiendo algunos caracteres, por ejemplo, si escribe el principio de un identificador como "using". Normalmente se cierra al presionar la tecla BARRA ESPACIADORA, Tab o ENTRAR para confirmar la selección. Puede implementar las características de IntelliSense que se desencadenan al escribir un carácter con un controlador de comandos para las pulsaciones de teclas \(el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz\) y un proveedor de controlador que implementa el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de finalización, que es la lista de identificadores que participan en la finalización, implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaz y un proveedor de código fuente de finalización \(el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfaz\). Los proveedores son componentes de Managed Extensibility Framework \(MEF\). Son responsables de las clases de origen y el controlador de exportación e importación de los servicios y los agentes, por ejemplo, el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite el desplazamiento del búfer de texto y <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, que desencadena la sesión de finalización.  
  
 Este tutorial muestra cómo implementar la finalización de instrucciones para un conjunto codificado de forma rígida de identificadores. En implementaciones completas, el servicio de lenguaje y la documentación del lenguaje son responsables de proporcionar ese contenido.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto MEF  
  
#### Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de VSIX de C\#. \(En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C\# \/ extensibilidad**, a continuación, **proyecto VSIX**.\) El nombre de la solución `CompletionTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulta [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
4.  Agregue las referencias siguientes al proyecto y asegúrese de que **CopyLocal** está establecido en `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Implementar el origen de finalización  
 El origen de finalización es responsable de recopilar el conjunto de identificadores y agregar el contenido a la ventana de finalización cuando un usuario escribe un desencadenador de finalización, como las primeras letras de un identificador. En este ejemplo, los identificadores y sus descripciones están codificados en la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> \(método\). En la mayoría de los usos reales, utilizaría el analizador de su idioma para obtener los tokens para rellenar la lista de finalización.  
  
#### Para implementar el origen de finalización  
  
1.  Agregue un archivo de clase y asígnele el nombre `TestCompletionSource`.  
  
2.  Agregue estas importaciones:  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modifique la declaración de clase de `TestCompletionSource` para que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Agregue campos privados para el proveedor de origen, el búfer de texto y una lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos \(que corresponden a los identificadores que participarán en la sesión de finalización\):  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Agregue un constructor que establece el búfer y el proveedor de origen. La `TestCompletionSourceProvider` clase se define en los pasos siguientes:  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método agregando un conjunto de finalización que contiene las finalizaciones desea proporcionar en el contexto. Cada conjunto de finalización contiene un conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> finalizaciones y corresponde a una ficha de la ventana de finalización. \(En proyectos de Visual Basic, se denominan las fichas de la ventana de finalización **común** y **todos los**.\) El método FindTokenSpanAtPosition se define en el paso siguiente.  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  El siguiente método se utiliza para buscar la palabra actual desde la posición del cursor:  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implemente el `Dispose()` método:  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## Implementar un proveedor de origen de finalización  
 El proveedor de origen de finalización es la parte del componente MEF que crea una instancia del origen de la finalización.  
  
#### Para implementar el proveedor de origen de finalización  
  
1.  Agregue una clase denominada `TestCompletionSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportar esta clase con una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto simple" y un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "finalización de prueba".  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importar un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que se usa para buscar la palabra actual en el origen de la finalización.  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> método para crear una instancia del origen de la finalización.  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## Implementar el proveedor de controlador de comandos de finalización  
 El proveedor de controlador de comandos de finalización se deriva un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, que escucha un evento de creación de la vista de texto y convierte la vista de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>que permite agregar el comando a la cadena de comando del shell de Visual Studio, a un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Dado que esta clase es una exportación MEF, también puede usarla para importar los servicios requeridos por el propio controlador de comandos.  
  
#### Para implementar el proveedor de controlador de comandos de finalización  
  
1.  Agregue un archivo denominado `TestCompletionCommandHandler`.  
  
2.  Agregue estas instrucciones using:  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Agregue una clase denominada `TestCompletionHandlerProvider` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportar esta clase con una <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "controlador de finalización token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto sin formato" y un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, que permite la conversión de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, y un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> que permite el acceso a los servicios estándar de Visual Studio.  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método para crear una instancia del controlador de comandos.  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## Implementar el controlador de comandos de finalización  
 Dado que las pulsaciones de tecla desencadena la finalización de instrucciones, debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para recibir y procesar las pulsaciones de teclas que desencadenan, confirmarán y cerrar la sesión de finalización.  
  
#### Para implementar el controlador de comandos de finalización  
  
1.  Agregue una clase denominada `TestCompletionCommandHandler` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Agregue campos privados para el siguiente controlador de comandos \(al que pasar el comando\), la vista de texto, el proveedor del controlador de comandos \(que permite el acceso a diversos servicios\) y una sesión de finalización:  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Agregue un constructor que establece la vista de texto y los campos del proveedor y el comando se agrega a la cadena de comando:  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método pasando el comando a lo largo de:  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implemente el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Cuando este método recibe una pulsación de tecla, debe hacer una de estas cosas:  
  
    -   Permitir que el carácter que se escribe en el búfer y, a continuación, desencadenar o filtrar la finalización. \(Caracteres imprimibles hacen esto\).  
  
    -   Confirmar la finalización, pero no permiten el carácter que se escribe en el búfer. \(Espacio en blanco, Tab y ENTRAR hacen cuando se muestra una sesión de finalización.\)  
  
    -   Permitir que el comando para pasar al siguiente controlador. \(Todos los demás comandos.\)  
  
     Dado que este método puede mostrar la interfaz de usuario, llamar a <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> para asegurarse de que no se llama en un contexto de automatización:  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Este código es un método privado que activa la sesión de finalización:  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  El siguiente ejemplo es un método privado que cancela la suscripción desde el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> eventos:  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## Compilar y probar el código  
 Para probar este código, compile la solución CompletionTest y ejecútelo en la instancia experimental.  
  
#### Para compilar y probar la solución CompletionTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba el texto que incluye la palabra "add".  
  
4.  A medida que escribe primero "a" y, a continuación, "d", debe mostrarse una lista que contiene "suma" y "adaptación". Observe que suma está seleccionada. Cuando se escribe otra "d", la lista debe contener sólo "suma", lo que está seleccionado. Puede confirmar "suma" presionando la tecla BARRA ESPACIADORA, Tab o Intro o descartar la lista escribiendo Esc o cualquier otra tecla.  
  
## Vea también  
 [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)