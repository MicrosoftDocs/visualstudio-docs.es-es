---
title: "Tutorial: Mostrar la Ayuda de firma | Microsoft Docs"
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
  - "editores [Visual Studio SDK] nuevos - información de ayuda o parámetro de firma"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Tutorial: Mostrar la Ayuda de firma
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ayuda para las firmas \(también conocido como *información de parámetros*\) muestra la firma de un método en una información sobre herramientas cuando el usuario escribe el carácter de inicio de lista de parámetros \(normalmente un paréntesis de apertura\). Como se escriben un parámetro y un separador de parámetros \(normalmente una coma\), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita. Puede definir la firma ayuda en el contexto de un servicio de lenguaje, puede definir su propio tipo de contenido y la extensión de nombre de archivo y mostrar la Ayuda de firma de ese tipo o puede mostrar la Ayuda de firma para un tipo de contenido existente \(por ejemplo, "text"\). Este tutorial muestra cómo mostrar la Ayuda de firma para el tipo de contenido "text".  
  
 Normalmente se activa la ayuda para las firmas escribiendo un carácter específico, por ejemplo, "\(" \(paréntesis de apertura\) y se descartan escribiendo otro carácter, por ejemplo, "\)" \(paréntesis de cierre\). Características de IntelliSense que se desencadenan escribiendo un carácter se pueden implementar mediante un controlador de comandos para las pulsaciones de teclas \(el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz\) y un proveedor de controlador que implementa el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaz. Para crear el origen de la Ayuda de firma, que es la lista de firmas que participan en la Ayuda de firma, implementar la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaz y un proveedor de código fuente que implementa el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaz. Los proveedores son componentes de Managed Extensibility Framework \(MEF\) y son responsables de las clases de origen y el controlador de exportación e importación de los servicios y los agentes, por ejemplo, el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite navegar en el búfer de texto, y <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, que desencadena la sesión de Ayuda de firma.  
  
 Este tutorial muestra cómo implementar la Ayuda de firma para un conjunto codificado de forma rígida de identificadores. En implementaciones completas, el lenguaje es responsable de proporcionar ese contenido.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto MEF  
  
#### Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de VSIX de C\#. \(En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C\# \/ extensibilidad**, a continuación, **proyecto VSIX**.\) El nombre de la solución `SignatureHelpTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulta [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
4.  Agregue las referencias siguientes al proyecto y asegúrese de que **CopyLocal** está establecido en `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Implementación de firma ayuda firmas y parámetros  
 El origen de la Ayuda de firma se basa en las firmas que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, cada uno de los cuales contiene parámetros que implementan <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. En una implementación completa, esta información se obtiene de la documentación del lenguaje, pero en este ejemplo, las firmas están codificados de forma rígida.  
  
#### Para implementar la Ayuda de firma firmas y parámetros  
  
1.  Agregue un archivo de clase y asígnele el nombre `SignatureHelpSource`.  
  
2.  Agregue las siguientes importaciones.  
  
     [!CODE [VSSDKSignatureHelpTest#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#1)]  
  
3.  Agregue una clase denominada `TestParameter` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!CODE [VSSDKSignatureHelpTest#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#2)]  
  
4.  Agregue un constructor que establece todas las propiedades.  
  
     [!CODE [VSSDKSignatureHelpTest#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#3)]  
  
5.  Agregar las propiedades de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!CODE [VSSDKSignatureHelpTest#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#4)]  
  
6.  Agregue una clase denominada `TestSignature` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!CODE [VSSDKSignatureHelpTest#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#5)]  
  
7.  Agregue algunos campos privados.  
  
     [!CODE [VSSDKSignatureHelpTest#6](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#6)]  
  
8.  Agregue un constructor que establece los campos y se suscribe a la <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos.  
  
     [!CODE [VSSDKSignatureHelpTest#7](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#7)]  
  
9. Declarar un `CurrentParameterChanged` eventos. Este evento se desencadena cuando el usuario rellene en uno de los parámetros de la firma.  
  
     [!CODE [VSSDKSignatureHelpTest#8](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#8)]  
  
10. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propiedad, por lo que TI provoca la `CurrentParameterChanged` eventos cuando se cambia el valor de propiedad.  
  
     [!CODE [VSSDKSignatureHelpTest#9](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#9)]  
  
11. Agregue un método que genera el `CurrentParameterChanged` eventos.  
  
     [!CODE [VSSDKSignatureHelpTest#10](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#10)]  
  
12. Agregue un método que calcula el parámetro actual comparando el número de comas en el <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> al número de comas en la firma.  
  
     [!CODE [VSSDKSignatureHelpTest#11](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#11)]  
  
13. Agregar un controlador de eventos para el <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento que llama el `ComputeCurrentParameter()` método.  
  
     [!CODE [VSSDKSignatureHelpTest#12](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#12)]  
  
14. Implemente la propiedad <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Esta propiedad contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> que corresponde al intervalo de texto en el búfer al que se aplica la firma.  
  
     [!CODE [VSSDKSignatureHelpTest#13](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#13)]  
  
15. Implemente los otros parámetros.  
  
     [!CODE [VSSDKSignatureHelpTest#14](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#14)]  
  
## Implementar el origen de la Ayuda de firma  
 El origen de la Ayuda de firma es el conjunto de firmas para el que se proporciona información.  
  
#### Para implementar el origen de la Ayuda de firma  
  
1.  Agregue una clase denominada `TestSignatureHelpSource` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!CODE [VSSDKSignatureHelpTest#15](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#15)]  
  
2.  Agregue una referencia al búfer de texto.  
  
     [!CODE [VSSDKSignatureHelpTest#16](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#16)]  
  
3.  Agregue un constructor que establece el búfer de texto y el proveedor de código fuente de la Ayuda de firma.  
  
     [!CODE [VSSDKSignatureHelpTest#17](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#17)]  
  
4.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. En este ejemplo, las firmas están codificados, pero en una implementación completa debería obtener esta información de la documentación del lenguaje.  
  
     [!CODE [VSSDKSignatureHelpTest#18](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#18)]  
  
5.  El método auxiliar `CreateSignature()` se proporciona sólo con fines ilustrativos.  
  
     [!CODE [VSSDKSignatureHelpTest#19](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#19)]  
  
6.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. En este ejemplo, hay sólo dos firmas, cada uno de los cuales tiene dos parámetros. Por lo tanto, este método no es necesario. En una implementación más completa, en el que más de un origen de la Ayuda de firma está disponible, este método se utiliza para decidir si el origen de ayuda para las signaturas de prioridad más alta puede proporcionar una firma coincidente. En caso contrario, el método devuelve null y el origen de la siguiente prioridad más alta se le pide que proporcione a una coincidencia.  
  
     [!CODE [VSSDKSignatureHelpTest#20](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#20)]  
  
7.  Implemente el método Dispose\(\):  
  
     [!CODE [VSSDKSignatureHelpTest#21](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#21)]  
  
## Implementar el proveedor de origen de la Ayuda de firma  
 El proveedor de código fuente de la Ayuda de firma es responsable para exportar la parte del componente de Managed Extensibility Framework \(MEF\) y para crear una instancia del origen de la Ayuda de firma.  
  
#### Para implementar el proveedor de código fuente de la Ayuda de firma  
  
1.  Agregue una clase denominada `TestSignatureHelpSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, y se exporta con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto" y un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes \= "default".  
  
     [!CODE [VSSDKSignatureHelpTest#22](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#22)]  
  
2.  Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando el `TestSignatureHelpSource`.  
  
     [!CODE [VSSDKSignatureHelpTest#23](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#23)]  
  
## Implementar el controlador de comandos  
 Ayuda para las firmas normalmente se activa por un \(carácter y descartadas por un\) caracteres. Puede controlar estas combinaciones de teclas implementando un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para que se desencadene una sesión de Ayuda de la firma cuando recibe un \(carácter precedido por un nombre de método conocido y descarta la sesión cuando recibe un\) caracteres.  
  
#### Para implementar el controlador de comandos  
  
1.  Agregue una clase denominada `TestSignatureHelpCommand` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!CODE [VSSDKSignatureHelpTest#24](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#24)]  
  
2.  Agregue campos privados para el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador \(que le permite agregar el controlador de comandos a los controladores de la cadena de comando\), la vista de texto, el agente de Ayuda de firma y sesión, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, y la siguiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!CODE [VSSDKSignatureHelpTest#25](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#25)]  
  
3.  Agregue un constructor para inicializar estos campos y agregar el filtro de comandos a los filtros de la cadena de comando.  
  
     [!CODE [VSSDKSignatureHelpTest#26](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#26)]  
  
4.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para desencadenar la sesión de Ayuda de la firma cuando se recibe el filtro de comandos un \(carácter después de que uno de los nombres de método conocido y para cerrar la sesión cuando recibe un\) carácter mientras la sesión está activa. En cada caso, se envía el comando.  
  
     [!CODE [VSSDKSignatureHelpTest#27](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#27)]  
  
5.  Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método por lo que TI siempre envía el comando.  
  
     [!CODE [VSSDKSignatureHelpTest#28](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#28)]  
  
## Implementar el proveedor de comandos de la Ayuda de firma  
 Puede proporcionar el comando Help firma implementando la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> crear instancias del controlador de comando cuando se crea la vista de texto.  
  
#### Para implementar el proveedor de comando Ayuda de firma  
  
1.  Agregue una clase denominada `TestSignatureHelpController` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> y se exporta con el <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, y <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!CODE [VSSDKSignatureHelpTest#29](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#29)]  
  
2.  Importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(usado para obtener el <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, dado el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto\), el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> \(que se usa para buscar la palabra actual\) y <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> \(para desencadenar la sesión de Ayuda de firma\).  
  
     [!CODE [VSSDKSignatureHelpTest#30](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#30)]  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método de creación de instancias de la `TestSignatureCommandHandler`.  
  
     [!CODE [VSSDKSignatureHelpTest#31](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#31)]  
  
## Compilar y probar el código  
 Para probar este código, compile la solución SignatureHelpTest y ejecútelo en la instancia experimental.  
  
#### Para compilar y probar la solución SignatureHelpTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Crear un archivo de texto y escriba algún texto que incluye la palabra "Agregar" Además de un paréntesis de apertura.  
  
4.  Después de escribir el paréntesis de apertura, debería ver una información sobre herramientas que muestra una lista de las dos firmas para el `add()` \(método\).  
  
## Vea también  
 [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)