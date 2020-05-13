---
title: 'Tutorial: Visualización de la ayuda de la firma ( S. Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697428"
---
# <a name="walkthrough-display-signature-help"></a>Tutorial: Mostrar la Ayuda de firma
La Ayuda de firma (también conocida como *Información de parámetros*) muestra la firma de un método en una información sobre herramientas cuando un usuario escribe el carácter de inicio de la lista de parámetros (normalmente un paréntesis de apertura). Como se escribe un parámetro y un separador de parámetros (normalmente una coma), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita. Puede definir la Ayuda de firma de las siguientes maneras: en el contexto de un servicio de lenguaje, definir su propia extensión de nombre de archivo y tipo de contenido y mostrar la Ayuda de firma solo para ese tipo, o mostrar la Ayuda de firma para un tipo de contenido existente (por ejemplo, "texto"). En este tutorial se muestra cómo mostrar la Ayuda de firma para el tipo de contenido "texto".

 La Ayuda de firma normalmente se desencadena escribiendo un carácter específico, por ejemplo, "(" (entre paréntesis de apertura) y se descarta escribiendo otro carácter, por ejemplo, ")" (paréntesis de cierre). Las características de IntelliSense que se desencadenan escribiendo un carácter se <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pueden implementar mediante un controlador <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> de comandos para las pulsaciones de teclas (la interfaz) y un proveedor de controlador que implementa la interfaz. Para crear el origen de la Ayuda de firma, que es <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> la lista de firmas <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> que participan en la Ayuda de firma, implemente la interfaz y un proveedor de origen que ejecute la interfaz. Los proveedores son componentes de Managed Extensibility Framework (MEF) y son responsables de exportar las <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>clases de origen y controlador e <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>importar servicios y intermediarios, por ejemplo, el , que le permite navegar en el búfer de texto, y el , que desencadena la sesión de ayuda de firma.

 En este tutorial se muestra cómo configurar la Ayuda de firma para un conjunto de identificadores codificado de forma rígida. En las implementaciones completas, el lenguaje es responsable de proporcionar ese contenido.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="creating-a-mef-project"></a>Creación de un proyecto MEF

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `SignatureHelpTest`nombre a la solución .

2. Agregue una plantilla de elemento Clasificador de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

4. Agregue las siguientes referencias al proyecto y asegúrese `false`de que **CopyLocal** está establecido en :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementar firmas y parámetros de la Ayuda de firmas
 El origen de la Ayuda de <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>firma se basa en <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>las firmas que implementan, cada una de las cuales contiene parámetros que implementan . En una implementación completa, esta información se obtendría de la documentación del lenguaje, pero en este ejemplo, las firmas están codificadas de forma rígida.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar las firmas y los parámetros de la Ayuda de firma

1. Agregue un archivo de clase y asígnele el nombre `SignatureHelpSource`.

2. Agregue las importaciones siguientes.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Agregue una `TestParameter` clase denominada <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>que implemente .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Agregue un constructor que establezca todas las propiedades.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Agregue las <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>propiedades de .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Agregue una `TestSignature` clase denominada <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>que implemente .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Agregue algunos campos privados.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Agregue un constructor que establezca los <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> campos y se suscriba al evento.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Declarar `CurrentParameterChanged` un evento. Este evento se produce cuando el usuario rellena uno de los parámetros de la firma.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> la propiedad para que `CurrentParameterChanged` genere el evento cuando se cambia el valor de la propiedad.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Agregue un método que `CurrentParameterChanged` genere el evento.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Agregue un método que calcule el parámetro actual comparando <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> el número de comas en el número de comas de la firma.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Agregue un controlador <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> de eventos `ComputeCurrentParameter()` para el evento que llama al método.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implemente la propiedad <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Esta propiedad contiene <xref:Microsoft.VisualStudio.Text.ITrackingSpan> un que corresponde al intervalo de texto en el búfer al que se aplica la firma.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implemente los demás parámetros.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementar el origen de la Ayuda de firma
 El origen de la Ayuda de firma es el conjunto de firmas para las que se proporciona información.

#### <a name="to-implement-the-signature-help-source"></a>Para implementar el origen de la Ayuda de firma

1. Agregue una `TestSignatureHelpSource` clase denominada <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>que implemente .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Agregue una referencia al búfer de texto.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Agregue un constructor que establezca el búfer de texto y el proveedor de origen de la Ayuda de firma.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. En este ejemplo, las firmas están codificadas de forma rígida, pero en una implementación completa obtendrá esta información de la documentación del lenguaje.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. El método `CreateSignature()` auxiliar se proporciona solo para la ilustración.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. En este ejemplo, hay solo dos firmas, cada una de las cuales tiene dos parámetros. Por lo tanto, este método no es necesario. En una implementación más completa, en la que hay más de un origen de Ayuda de firma disponible, este método se usa para decidir si el origen de Ayuda de firma de mayor prioridad puede proporcionar una firma coincidente. Si no puede, el método devuelve null y se pide al origen de prioridad más siguiente que proporcione una coincidencia.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implemente `Dispose()` el método:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementar el proveedor de origen de la Ayuda de firma
 El proveedor de origen de la Ayuda de firma es responsable de exportar la parte del componente Managed Extensibility Framework (MEF) y de crear instancias del origen de la Ayuda de firma.

#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar el proveedor de origen de la Ayuda de firma

1. Agregue una `TestSignatureHelpSourceProvider` clase denominada <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>que implemente y <xref:Microsoft.VisualStudio.Utilities.NameAttribute>expórtela con un , un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text" y un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before-"default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando un `TestSignatureHelpSource`archivo .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementar el controlador de comandos
 La Ayuda de firma normalmente se desencadena por un paréntesis de apertura "(" carácter y se descarta por un paréntesis de cierre ")". Puede controlar estas pulsaciones de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> teclas ejecutando un para que desencadene una sesión de Ayuda de firma cuando recibe un carácter de paréntesis de apertura precedido por un nombre de método conocido y descarta la sesión cuando recibe un carácter de paréntesis de cierre.

#### <a name="to-implement-the-command-handler"></a>Para implementar el controlador de comandos

1. Agregue una `TestSignatureHelpCommand` clase denominada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>que implemente .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Agregue campos privados para el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador (que le permite agregar el controlador de comandos a la <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>cadena de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>controladores de comandos), la vista de texto, el intermediario y la sesión de la Ayuda de firma, un , y el siguiente .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Agregue un constructor para inicializar estos campos y agregar el filtro de comandos a la cadena de filtros de comandos.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> el método para desencadenar la sesión de Ayuda de firma cuando el filtro de comandos recibe un paréntesis de apertura "(" carácter después de uno de los nombres de método conocidos y para descartar la sesión cuando recibe un paréntesis de cierre ")" carácter mientras la sesión sigue activa. En todos los casos, se reenvía el comando.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> el método para que siempre reenvíe el comando.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementar el proveedor de comandos de ayuda de firma
 Puede proporcionar el comando Ayuda <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> de firma implementando la instancia del controlador de comandos cuando se crea la vista de texto.

### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar el proveedor de comandos de la Ayuda de firma

1. Agregue una `TestSignatureHelpController` clase denominada <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> que la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>implemente <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>y <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>expórtela con , , y .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importe <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> el (utilizado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>para obtener <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , dado el objeto), el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (utilizado para buscar la palabra actual) y el (para desencadenar la sesión de Ayuda de firma).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implemente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> el método creando una `TestSignatureCommandHandler`instancia de .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Construir y probar el código
 Para probar este código, compile la solución SignatureHelpTest y ejecútela en la instancia experimental.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para compilar y probar la solución SignatureHelpTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto que incluya la palabra "añadir" más un paréntesis de apertura.

4. Después de escribir el paréntesis de apertura, debería ver una información sobre `add()` herramientas que muestra una lista de las dos firmas para el método.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
