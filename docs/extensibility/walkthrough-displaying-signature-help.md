---
title: 'Tutorial: Mostrar la ayuda de las firmas | Microsoft Docs'
description: Obtenga información sobre cómo mostrar la ayuda de firmas para el tipo de contenido de texto mediante este tutorial. Ayuda para las firmas muestra la firma de un método en una información sobre herramientas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6ffa2a0e646c11cb56d08ef91e3d7a4b9af7572
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217507"
---
# <a name="walkthrough-display-signature-help"></a>Tutorial: Mostrar ayuda para las firmas
La ayuda para las firmas (también conocida como *información de parámetros*) muestra la firma de un método en una información sobre herramientas cuando un usuario escribe el carácter de inicio de la lista de parámetros (normalmente un paréntesis de apertura). Como parámetro y el separador de parámetros (normalmente una coma) se escriben, la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita. Puede definir la ayuda de la firma de las siguientes maneras: en el contexto de un servicio de lenguaje, defina su propia extensión de nombre de archivo y el tipo de contenido, así como la ayuda para mostrar la firma solo para ese tipo o para mostrar la ayuda de las firmas para un tipo de contenido existente (por ejemplo, "texto"). En este tutorial se muestra cómo mostrar la ayuda de las firmas para el tipo de contenido "texto".

 La ayuda para las firmas se desencadena normalmente escribiendo un carácter concreto, por ejemplo, "(" (paréntesis de apertura) y descartado escribiendo otro carácter, por ejemplo, ")" (paréntesis de cierre). Las características de IntelliSense que se desencadenan escribiendo un carácter se pueden implementar mediante un controlador de comandos para las pulsaciones de teclas (la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz) y un proveedor de controladores que implementa la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de la ayuda para las firmas, que es la lista de firmas que participan en la ayuda para las firmas, implemente la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaz y un proveedor de origen que ejecute la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaz. Los proveedores son partes de componentes de Managed Extensibility Framework (MEF) y son responsables de exportar las clases de origen y de controlador, e importar los servicios y los agentes, por ejemplo,, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> que le permite navegar por el búfer de texto y <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , que desencadena la sesión de ayuda para las firmas.

 En este tutorial se muestra cómo configurar la ayuda para las firmas para un conjunto de identificadores codificados de forma rígida. En las implementaciones completas, el idioma es responsable de proporcionar ese contenido.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Crear un proyecto MEF

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad** y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `SignatureHelpTest` .

2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

4. Agregue las siguientes referencias al proyecto y asegúrese de que **CopyLocal** está establecido en `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft. VisualStudio. Shell. 14.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementar firmas y parámetros de ayuda para las firmas
 El origen de la ayuda para las firmas se basa en las firmas que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , cada una de las cuales contiene los parámetros que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . En una implementación completa, esta información se obtiene de la documentación del lenguaje, pero en este ejemplo, las firmas están codificadas de forma rígida.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar las firmas y los parámetros de ayuda para las firmas

1. Agregue un archivo de clase y asígnele el nombre `SignatureHelpSource`.

2. Agregue las importaciones siguientes.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet1":::

3. Agregue una clase denominada `TestParameter` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet2":::

4. Agregue un constructor que establezca todas las propiedades.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet3":::

5. Agregue las propiedades de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet4":::

6. Agregue una clase denominada `TestSignature` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet5":::

7. Agregue algunos campos privados.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet6":::

8. Agregue un constructor que establezca los campos y se suscriba al <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet7":::

9. Declare un `CurrentParameterChanged` evento. Este evento se desencadena cuando el usuario rellena uno de los parámetros de la firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet8":::

10. Implemente la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propiedad para que genere el `CurrentParameterChanged` evento cuando cambie el valor de la propiedad.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet9":::

11. Agregue un método que genere el `CurrentParameterChanged` evento.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet10":::

12. Agregue un método que calcule el parámetro actual comparando el número de comas del <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> con el número de comas de la firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet11":::

13. Agregue un controlador de eventos para el <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento que llama al `ComputeCurrentParameter()` método.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet12":::

14. Implemente la propiedad <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Esta propiedad contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> que corresponde al intervalo de texto del búfer al que se aplica la firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet13":::

15. Implemente los otros parámetros.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet14":::

## <a name="implement-the-signature-help-source"></a>Implementar el origen de la ayuda para las firmas
 El origen de la ayuda para las firmas es el conjunto de firmas para el que se proporciona información.

#### <a name="to-implement-the-signature-help-source"></a>Para implementar el origen de la ayuda para las firmas

1. Agregue una clase denominada `TestSignatureHelpSource` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet15":::

2. Agregue una referencia al búfer de texto.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet16":::

3. Agregue un constructor que establezca el búfer de texto y el proveedor de origen de la ayuda para las firmas.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet17":::

4. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. En este ejemplo, las firmas están codificadas de forma rígida, pero, en una implementación completa, obtendría esta información en la documentación del lenguaje.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet18":::

5. El método auxiliar `CreateSignature()` se proporciona solo para la ilustración.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet19":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet19":::

6. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. En este ejemplo, hay solo dos firmas, cada una de las cuales tiene dos parámetros. Por lo tanto, este método no es necesario. En una implementación más completa, en la que hay más de un origen de ayuda para las firmas disponible, este método se usa para decidir si el origen de ayuda de la firma de prioridad más alta puede proporcionar una firma coincidente. Si no es posible, el método devuelve NULL y se pide al siguiente origen de prioridad más alto que proporcione una coincidencia.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet20":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet20":::

7. Implemente el `Dispose()` método:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet21":::

## <a name="implement-the-signature-help-source-provider"></a>Implementar el proveedor de origen de la ayuda para las firmas
 El proveedor de origen de la ayuda para las firmas es responsable de exportar la parte del componente Managed Extensibility Framework (MEF) y de crear instancias del origen de la ayuda para las firmas.

#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar el proveedor de origen de la ayuda para las firmas

1. Agregue una clase denominada `TestSignatureHelpSourceProvider` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , y expórtelo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Text" y <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = "default".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet22":::

2. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> la instancia de `TestSignatureHelpSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet23":::

## <a name="implement-the-command-handler"></a>Implementar el controlador de comandos
 La ayuda para las firmas se desencadena normalmente mediante un paréntesis de apertura "(" y se descarta mediante un carácter de paréntesis de cierre ")". Puede controlar estas pulsaciones de teclas ejecutando un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto para que desencadene una sesión de ayuda para las firmas cuando reciba un carácter de paréntesis de apertura precedido por un nombre de método conocido y descarte la sesión cuando reciba un carácter de paréntesis de cierre.

#### <a name="to-implement-the-command-handler"></a>Para implementar el controlador de comandos

1. Agregue una clase denominada `TestSignatureHelpCommand` que implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet24":::

2. Agregue campos privados para el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador (que le permite agregar el controlador de comandos a la cadena de controladores de comandos), la vista de texto, la sesión y el agente de ayuda para las firmas, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> y el siguiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet25":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet25":::

3. Agregue un constructor para inicializar estos campos y agregar el filtro de comandos a la cadena de filtros de comandos.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet26":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet26":::

4. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para desencadenar la sesión de ayuda para las firmas cuando el filtro de comandos reciba un paréntesis de apertura "(" después de uno de los nombres de método conocidos y para descartar la sesión cuando reciba un paréntesis de cierre ")" mientras la sesión todavía esté activa. En todos los casos, se reenvía el comando.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet27":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet27":::

5. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para que siempre reenvíe el comando.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet28":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet28":::

## <a name="implement-the-signature-help-command-provider"></a>Implementar el proveedor de comandos de ayuda para las firmas
 Puede proporcionar el comando de ayuda para las firmas implementando <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para crear una instancia del controlador de comandos cuando se crea la vista de texto.

### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar el proveedor de comandos de ayuda para las firmas

1. Agregue una clase denominada `TestSignatureHelpController` que implemente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> y exporte con <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> y <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet29":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet29":::

2. Importe <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (se usa para obtener <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , dado el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto), (se <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> usa para buscar la palabra actual) y <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (para desencadenar la sesión de ayuda para las firmas).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet30":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet30":::

3. Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método mediante la creación de instancias de `TestSignatureCommandHandler` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet31":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet31":::

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución SignatureHelpTest y ejecútela en la instancia experimental.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para compilar y probar la solución SignatureHelpTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto que incluya la palabra "agregar" más un paréntesis de apertura.

4. Después de escribir el paréntesis de apertura, debería ver una información sobre herramientas que muestra una lista de las dos firmas para el `add()` método.

## <a name="see-also"></a>Consulte también
- [Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
