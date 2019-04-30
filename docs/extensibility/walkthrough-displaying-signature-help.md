---
title: 'Tutorial: Mostrar la Ayuda de signatura | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d81ee2e860dead62352cc14cef95e21536c29d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965172"
---
# <a name="walkthrough-display-signature-help"></a>Tutorial: Mostrar la Ayuda de firma
Ayuda para la firma (también conocido como *información de parámetros*) muestra la firma de un método en una información sobre herramientas cuando un usuario escribe el carácter de inicio de lista de parámetros (normalmente un paréntesis de apertura). Como se ha escrito un parámetro y el separador de parámetro (normalmente una coma), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita. Puede definir la Ayuda de signatura de las siguientes maneras: en el contexto de un servicio de lenguaje, definir su propia extensión de nombre de archivo y el tipo de contenido y mostrar la Ayuda de firma para solo ese tipo o mostrar la Ayuda de firma para un tipo de contenido existente (por ejemplo, "text"). En este tutorial se muestra cómo mostrar la Ayuda de signatura para el tipo de contenido "text".

 Normalmente se activa la Ayuda de signatura escribiendo un carácter específico, por ejemplo, "(" (paréntesis de apertura) y se descartan escribiendo otro carácter, por ejemplo, ")" (paréntesis de cierre). Las características de IntelliSense que se desencadenan escribiendo un carácter pueden implementarse mediante el uso de un controlador de comandos para las pulsaciones de teclas (el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz) y un proveedor del controlador que implementa el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de Ayuda de signatura, que es la lista de firmas que participan en la Ayuda de signatura, implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaz y un proveedor de código fuente que se ejecuta el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaz. Los proveedores son partes de componentes de Managed Extensibility Framework (MEF) y son responsables de las clases de origen y el controlador de exportación e importación de los servicios y los agentes, por ejemplo, el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite navegar en el búfer de texto y el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, lo que desencadena la sesión de Ayuda de signatura.

 Este tutorial muestra cómo configurar la Ayuda de firma para un conjunto codificado de forma rígida de identificadores. En implementaciones completas, el lenguaje es responsable de proporcionar ese contenido.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Creación de un proyecto MEF

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `SignatureHelpTest`.

2. Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

4. Agregue las siguientes referencias al proyecto y asegúrese de que **CopyLocal** está establecido en `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementar firmas de Ayuda de signatura y parámetros
 El origen de la Ayuda de signatura se basa en las firmas que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, cada uno de los cuales contiene los parámetros que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. En una implementación completa, esta información se obtiene con la documentación del lenguaje, pero en este ejemplo, las firmas están codificados de forma rígida.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar la Ayuda de signatura firmas y los parámetros

1. Agregue un archivo de clase y asígnele el nombre `SignatureHelpSource`.

2. Agregue las siguientes importaciones.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Agregue una clase denominada `TestParameter` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Agregue un constructor que establece todas las propiedades.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Agregue las propiedades de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Agregue una clase denominada `TestSignature` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Agregue algunos campos privados.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Agregue un constructor que establece los campos y se suscribe a la <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Declarar un `CurrentParameterChanged` eventos. Este evento se desencadena cuando el usuario se rellene en uno de los parámetros de la firma.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propiedad, por lo que TI provoca la `CurrentParameterChanged` eventos cuando se cambia el valor de propiedad.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Agregue un método que genera el `CurrentParameterChanged` eventos.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Agregue un método que calcula el parámetro actual comparando el número de comas en el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> al número de comas en la firma.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Agregar un controlador de eventos para el <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento que llama el `ComputeCurrentParameter()` método.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implemente la propiedad <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Esta propiedad contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> que corresponde al intervalo de texto en el búfer al que se aplica la firma.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementar los demás parámetros.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementar el origen de la Ayuda de signatura
 El origen de la Ayuda de signatura es el conjunto de firmas para el que proporcionar información.

#### <a name="to-implement-the-signature-help-source"></a>Para implementar el origen de la Ayuda de signatura

1. Agregue una clase denominada `TestSignatureHelpSource` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Agregue una referencia al búfer de texto.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Agregue un constructor que establece el búfer de texto y el proveedor de código fuente de Ayuda de signatura.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. En este ejemplo, las firmas están codificados, pero en una implementación completa podría obtener esta información de la documentación del lenguaje.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. El método auxiliar `CreateSignature()` viene meramente ilustrativos.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. En este ejemplo, hay solo dos firmas, cada uno de los cuales tiene dos parámetros. Por lo tanto, este método no es necesario. En una implementación más completa, en el que más de un origen de Ayuda de signatura está disponible, este método se utiliza para decidir si el origen de Ayuda de signatura de prioridad más alta puede proporcionar una signatura coincidente. Si no es posible, el método devuelve null y el origen de la siguiente prioridad más alta se le pide que proporcione a una coincidencia.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implemente el `Dispose()` método:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementar el proveedor de código fuente de Ayuda de signatura
 El proveedor de código fuente de Ayuda de signatura es responsable para exportar la parte del componente de Managed Extensibility Framework (MEF) y para crear una instancia del origen de la Ayuda de signatura.

#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar el proveedor de código fuente de Ayuda de signatura

1. Agregue una clase denominada `TestSignatureHelpSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>y se exporta con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text" y un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = "default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando el `TestSignatureHelpSource`.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementar el controlador de comandos
 Ayuda para las firmas normalmente se desencadena por un paréntesis de apertura "(" carácter y descartadas por un paréntesis de cierre")" caracteres. Puede controlar estas pulsaciones de teclas mediante la ejecución de un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para que se desencadene una sesión de Ayuda de signatura cuando recibe una apertura paréntesis precedido por un nombre de método conocidos y descarta la sesión cuando recibe un cierre de paréntesis.

#### <a name="to-implement-the-command-handler"></a>Para implementar el controlador de comandos

1. Agregue una clase denominada `TestSignatureHelpCommand` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Agregar campos privados para el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador (que le permite agregar el controlador de comandos a los controladores de cadena de comandos), la vista de texto, el agente de Ayuda de signatura y sesión, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>y la siguiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Agregue un constructor para inicializar estos campos y agregar el filtro de comandos a la cadena de filtros de comandos.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para desencadenar la sesión de Ayuda de signatura cuando el filtro de comandos recibe un paréntesis de apertura carácter "(" carácter después de que uno de los nombres de método conocidos y para cerrar la sesión cuando recibe un paréntesis de cierre")" mientras la sesión está activa. En todos los casos, se reenvía el comando.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método por lo que TI siempre reenvía el comando.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementar el proveedor de comandos de Ayuda de signatura
 Puede proporcionar el comando de Ayuda de signatura implementando el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para crear el controlador de comandos cuando se crea la vista de texto.

### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar el proveedor de comandos de Ayuda de signatura

1. Agregue una clase denominada `TestSignatureHelpController` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> y exportarlo con la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, y <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (utilizado para obtener el <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, dado el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto), el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (que se utiliza para buscar la palabra actual) y el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (para desencadenar la sesión de Ayuda de signatura).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método creando el `TestSignatureCommandHandler`.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución SignatureHelpTest y ejecútelo en la instancia experimental.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para compilar y probar la solución SignatureHelpTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto que incluye la palabra "Agregar" Además de un paréntesis de apertura.

4. Después de escribir el paréntesis de apertura, debería ver una información sobre herramientas que muestra una lista de las dos firmas para el `add()` método.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)