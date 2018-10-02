---
title: 'Tutorial: Mostrar ayuda para las firmas | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24c3eea821209485b5d57335c0c948cae92b4a20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574961"
---
# <a name="walkthrough-displaying-signature-help"></a>Tutorial: Visualización de ayuda de signatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Tutorial: mostrar la Ayuda de signatura](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-displaying-signature-help).  
  
Ayuda para la firma (también conocido como *información de parámetros*) muestra la firma de un método en una información sobre herramientas cuando un usuario escribe el carácter de inicio de lista de parámetros (normalmente un paréntesis de apertura). Como se ha escrito un parámetro y el separador de parámetro (normalmente una coma), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita. Puede definir la Ayuda de signatura en el contexto de un servicio de lenguaje, o puede definir su propio tipo de contenido y la extensión de nombre de archivo y mostrar la Ayuda de signatura para solo ese tipo, o puede mostrar la Ayuda de signatura de un tipo de contenido existente (por ejemplo, "text"). En este tutorial se muestra cómo mostrar la Ayuda de signatura para el tipo de contenido "text".  
  
 Normalmente se activa la Ayuda de signatura escribiendo un carácter específico, por ejemplo, "(" (paréntesis de apertura) y se descartan escribiendo otro carácter, por ejemplo, ")" (paréntesis de cierre). Las características de IntelliSense que se desencadenan escribiendo un carácter pueden implementarse mediante el uso de un controlador de comandos para las pulsaciones de teclas (el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz) y un proveedor del controlador que implementa el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de Ayuda de signatura, que es la lista de firmas que participan en la Ayuda de signatura, implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaz y un proveedor de código fuente que implementa el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaz. Los proveedores son partes de componentes de Managed Extensibility Framework (MEF) y son responsables de las clases de origen y el controlador de exportación e importación de los servicios y los agentes, por ejemplo, el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite navegar en el búfer de texto y el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, lo que desencadena la sesión de Ayuda de signatura.  
  
 Este tutorial muestra cómo implementar la Ayuda de signatura para un conjunto codificado de forma rígida de identificadores. En implementaciones completas, el lenguaje es responsable de proporcionar ese contenido.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creación de un proyecto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Nombre de la solución `SignatureHelpTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
4.  Agregue las siguientes referencias al proyecto y asegúrese de que **CopyLocal** está establecido en `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementar firmas ayudan a las firmas y parámetros  
 El origen de la Ayuda de signatura se basa en las firmas que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, cada uno de los cuales contiene los parámetros que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. En una implementación completa, esta información se obtiene con la documentación del lenguaje, pero en este ejemplo, las firmas están codificados de forma rígida.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar la Ayuda de signatura firmas y los parámetros  
  
1.  Agregue un archivo de clase y asígnele el nombre `SignatureHelpSource`.  
  
2.  Agregue las siguientes importaciones.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3.  Agregue una clase denominada `TestParameter` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4.  Agregue un constructor que establece todas las propiedades.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5.  Agregue las propiedades de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6.  Agregue una clase denominada `TestSignature` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7.  Agregue algunos campos privados.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8.  Agregue un constructor que establece los campos y se suscribe a la <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Declarar un `CurrentParameterChanged` eventos. Este evento se desencadena cuando el usuario se rellene en uno de los parámetros de la firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propiedad, por lo que TI provoca la `CurrentParameterChanged` eventos cuando se cambia el valor de propiedad.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Agregue un método que genera el `CurrentParameterChanged` eventos.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Agregue un método que calcula el parámetro actual comparando el número de comas en el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> al número de comas en la firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Agregar un controlador de eventos para el <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento que llama el `ComputeCurrentParameter()` método.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implemente la propiedad <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Esta propiedad contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> que corresponde al intervalo de texto en el búfer al que se aplica la firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implementar los demás parámetros.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementar el origen de la Ayuda de firma  
 El origen de la Ayuda de signatura es el conjunto de firmas para el que proporcionar información.  
  
#### <a name="to-implement-the-signature-help-source"></a>Para implementar el origen de la Ayuda de signatura  
  
1.  Agregue una clase denominada `TestSignatureHelpSource` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2.  Agregue una referencia al búfer de texto.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3.  Agregue un constructor que establece el búfer de texto y el proveedor de código fuente de Ayuda de signatura.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. En este ejemplo, las firmas están codificados, pero en una implementación completa podría obtener esta información de la documentación del lenguaje.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5.  El método auxiliar `CreateSignature()` viene meramente ilustrativos.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. En este ejemplo, hay solo dos firmas, cada uno de los cuales tiene dos parámetros. Por lo tanto, este método no es necesario. En una implementación más completa, en el que más de un origen de Ayuda de signatura está disponible, este método se utiliza para decidir si el origen de Ayuda de signatura de prioridad más alta puede proporcionar una signatura coincidente. Si no es posible, el método devuelve null y el origen de la siguiente prioridad más alta se le pide que proporcione a una coincidencia.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7.  Implemente el método Dispose():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementar el proveedor de código fuente de Ayuda de firma  
 El proveedor de código fuente de Ayuda de signatura es responsable para exportar la parte del componente de Managed Extensibility Framework (MEF) y para crear una instancia del origen de la Ayuda de signatura.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar el proveedor de código fuente de Ayuda de signatura  
  
1.  Agregue una clase denominada `TestSignatureHelpSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>y se exporta con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text" y un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = "default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2.  Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando el `TestSignatureHelpSource`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementar el controlador de comandos  
 Ayuda para la firma es normalmente son activada por un (carácter y descartadas por un) caracteres. Puede controlar estas pulsaciones de teclas implementando un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para que se desencadene una sesión de Ayuda de signatura cuando recibe un (carácter precedido por un nombre de método conocidos y descarta la sesión cuando recibe un) caracteres.  
  
#### <a name="to-implement-the-command-handler"></a>Para implementar el controlador de comandos  
  
1.  Agregue una clase denominada `TestSignatureHelpCommand` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2.  Agregar campos privados para el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador (que le permite agregar el controlador de comandos a los controladores de cadena de comandos), la vista de texto, el agente de Ayuda de signatura y sesión, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>y la siguiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3.  Agregue un constructor para inicializar estos campos y agregar el filtro de comandos a la cadena de filtros de comandos.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para desencadenar la sesión de Ayuda de signatura cuando recibe el filtro de comandos un (carácter después de que uno de los nombres de método conocidos y para cerrar la sesión cuando recibe un) mientras está activa la sesión de caracteres. En todos los casos, se reenvía el comando.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método por lo que TI siempre reenvía el comando.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementar el proveedor de comandos de la Ayuda de firma  
 Puede proporcionar el comando de Ayuda de signatura implementando el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para crear el controlador de comandos cuando se crea la vista de texto.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar el proveedor de comandos de Ayuda de signatura  
  
1.  Agregue una clase denominada `TestSignatureHelpController` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> y exportarlo con la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, y <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2.  Importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (utilizado para obtener el <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, dado el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto), el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (que se utiliza para buscar la palabra actual) y el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (para desencadenar la sesión de Ayuda de signatura).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método creando el `TestSignatureCommandHandler`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución SignatureHelpTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para compilar y probar la solución SignatureHelpTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto que incluye la palabra "Agregar" Además de un paréntesis de apertura.  
  
4.  Después de escribir el paréntesis de apertura, debería ver una información sobre herramientas que muestra una lista de las dos firmas para el `add()` método.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

