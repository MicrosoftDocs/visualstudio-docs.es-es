---
title: 'Tutorial: Mostrar la finalización de instrucciones | Microsoft Docs'
description: Obtenga información sobre cómo implementar la finalización de instrucciones basada en lenguaje para el contenido de texto sin formato mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: leslierichardson95
ms.author: lerich
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 51281c261baf5744c1d3aa0903985a173ff240f2
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217481"
---
# <a name="walkthrough-display-statement-completion"></a>Tutorial: Mostrar la finalización de instrucciones
Puede implementar la finalización de instrucciones basada en el lenguaje si define los identificadores para los que desea proporcionar la finalización y, a continuación, desencadenar una sesión de finalización. Puede definir la finalización de instrucciones en el contexto de un servicio de lenguaje, definir su propia extensión de nombre de archivo y tipo de contenido y, a continuación, Mostrar la finalización solo para ese tipo. O bien, puede desencadenar la finalización de un tipo de contenido existente (por ejemplo, "Plaintext"). En este tutorial se muestra cómo desencadenar la finalización de instrucciones para el tipo de contenido "Plaintext", que es el tipo de contenido de los archivos de texto. El tipo de contenido "texto" es el antecesor de todos los demás tipos de contenido, incluidos los archivos de código y XML.

 La finalización de instrucciones se desencadena normalmente escribiendo ciertos caracteres (por ejemplo, al escribir el principio de un identificador como "Using"). Normalmente se descarta presionando la **barra espaciadora**, la **tabulación** o la tecla **entrar** para confirmar una selección. Puede implementar las características de IntelliSense que se desencadenan al escribir un carácter mediante un controlador de comandos para las pulsaciones de teclas (la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz) y un proveedor de controladores que implementa la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de finalización, que es la lista de identificadores que participan en la finalización, implemente la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaz y un proveedor de origen de finalización (la <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfaz). Los proveedores son partes de componentes de Managed Extensibility Framework (MEF). Son responsables de exportar las clases de origen y de controlador e importar los servicios y los agentes, por ejemplo, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , que permite la navegación en el búfer de texto y <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , que desencadena la sesión de finalización.

 En este tutorial se muestra cómo implementar la finalización de instrucciones para un conjunto de identificadores codificados de forma rígida. En las implementaciones completas, el servicio de lenguaje y la documentación del lenguaje son responsables de proporcionar ese contenido.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creación de un proyecto MEF

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad** y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `CompletionTest` .

2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

4. Agregue las siguientes referencias al proyecto y asegúrese de que **CopyLocal** está establecido en `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft. VisualStudio. Shell. 15.0

     Microsoft. VisualStudio. Shell. immutable. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Implementar el origen de finalización
 El origen de finalización es responsable de recopilar el conjunto de identificadores y de agregar el contenido a la ventana de finalización cuando un usuario escribe un desencadenador de finalización, como las primeras letras de un identificador. En este ejemplo, los identificadores y sus descripciones están codificados de forma rígida en el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método. En la mayoría de los usos del mundo real, se usaría el analizador del lenguaje para obtener los tokens para rellenar la lista de finalización.

### <a name="to-implement-the-completion-source"></a>Para implementar el origen de finalización

1. Agregue un archivo de clase y asígnele el nombre `TestCompletionSource`.

2. Agregue estas importaciones:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet1":::

3. Modifique la declaración de clase para para `TestCompletionSource` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet2":::

4. Agregue campos privados para el proveedor de origen, el búfer de texto y una lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos (que se corresponden con los identificadores que participarán en la sesión de finalización):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet3":::

5. Agregue un constructor que establezca el proveedor y el búfer de origen. La `TestCompletionSourceProvider` clase se define en pasos posteriores:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet4":::

6. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método agregando un conjunto de finalización que contenga las finalizaciones que desea proporcionar en el contexto. Cada conjunto de finalización contiene un conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> finalizaciones y corresponde a una pestaña de la ventana de finalización. (En proyectos de Visual Basic, las pestañas de la ventana de finalización se denominan **común** y **todos**). El `FindTokenSpanAtPosition` método se define en el paso siguiente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet5":::

7. El método siguiente se usa para buscar la palabra actual desde la posición del cursor:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet6":::

8. Implemente el `Dispose()` método:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet7":::

## <a name="implement-the-completion-source-provider"></a>Implementar el proveedor de origen de finalización
 El proveedor de origen de finalización es la parte del componente de MEF que crea una instancia del origen de finalización.

### <a name="to-implement-the-completion-source-provider"></a>Para implementar el proveedor de origen de finalización

1. Agregue una clase denominada `TestCompletionSourceProvider` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Exporte esta clase con <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Plaintext" y un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "finalización de prueba".

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet8":::

2. Importe un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , que busca la palabra actual en el origen de finalización.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet9":::

3. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> método para crear una instancia del origen de finalización.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet10":::

## <a name="implement-the-completion-command-handler-provider"></a>Implementar el proveedor del controlador de comandos de finalización
 El proveedor del controlador de comandos de finalización se deriva de un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , que escucha un evento de creación de la vista de texto y convierte la vista de, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> que permite agregar el comando a la cadena de comandos de Visual Studio Shell, a <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Dado que esta clase es una exportación de MEF, también puede usarla para importar los servicios que requiere el propio controlador de comandos.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar el proveedor del controlador de comandos de finalización

1. Agregue un archivo denominado `TestCompletionCommandHandler` .

2. Agregue estas directivas Using:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet11":::

3. Agregue una clase denominada `TestCompletionHandlerProvider` que implemente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Exporte esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "controlador de finalización de token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Plaintext" y un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet12":::

4. Importe <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , que permite la conversión de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a,, <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> y a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> que permite el acceso a los servicios estándar de Visual Studio.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet13":::

5. Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método para crear una instancia del controlador de comandos.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet14":::

## <a name="implement-the-completion-command-handler"></a>Implementar el controlador de comandos de finalización
 Como la finalización de instrucciones se desencadena mediante pulsaciones de teclas, debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para recibir y procesar las pulsaciones de teclas que desencadenan, confirman y descartan la sesión de finalización.

#### <a name="to-implement-the-completion-command-handler"></a>Para implementar el controlador de comandos de finalización

1. Agregue una clase denominada `TestCompletionCommandHandler` que implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet15":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet15":::

2. Agregue campos privados para el siguiente controlador de comandos (al que se pasa el comando), la vista de texto, el proveedor del controlador de comandos (que permite el acceso a varios servicios) y una sesión de finalización:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet16":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet16":::

3. Agregue un constructor que establezca la vista de texto y los campos de proveedor, y agregue el comando a la cadena de comandos:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet17":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet17":::

4. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método pasando el comando a lo largo de:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet18":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet18":::

5. Implemente el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Cuando este método recibe una pulsación de tecla, debe realizar una de estas acciones:

   - Permita que el carácter se escriba en el búfer y, a continuación, desencadene o filtre la finalización. (Los caracteres de impresión lo hacen).

   - Confirma la finalización, pero no permite que el carácter se escriba en el búfer. (Espacio en blanco, **pestaña** y **Escriba** haga esto cuando se muestre una sesión de finalización).

   - Permite pasar el comando al siguiente controlador. (El resto de comandos).

     Dado que este método puede mostrar la interfaz de usuario, llame <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> a para asegurarse de que no se llama en un contexto de automatización:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet19":::

6. Este código es un método privado que desencadena la sesión de finalización:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet20":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet20":::

7. El ejemplo siguiente es un método privado que cancela la suscripción del <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet21":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet21":::

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución CompletionTest y ejecútela en la instancia experimental.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar y probar la solución CompletionTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto que incluya la palabra "agregar".

4. A medida que escribe primero "a" y luego "d", debe aparecer una lista que contiene "suma" y "adaptación". Observe que está seleccionada la opción adición. Cuando escribe otra "d", la lista solo debe contener "suma", que ahora está seleccionada. Puede confirmar "suma" presionando la **barra espaciadora**, la **tabulación** o la tecla **entrar** , o bien descartar la lista escribiendo ESC o cualquier otra tecla.

## <a name="see-also"></a>Consulte también
- [Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
