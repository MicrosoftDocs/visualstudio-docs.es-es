---
title: 'Tutorial: Mostrar las llaves coincidentes | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b1d6833a3dca2ce8b076574ecb4b9856a6e9d79
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998662"
---
# <a name="walkthrough-displaying-matching-braces"></a>Tutorial: Mostrar llaves que coincidan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar características basadas en lenguaje como definiendo las llaves que desee hacer coincidir y, a continuación, agregar una etiqueta de marcador de texto a las llaves coincidentes cuando el símbolo de intercalación está en una de las llaves la coincidencia de llaves. Puede definir las llaves en el contexto de un lenguaje, o puede definir su propio tipo de contenido y la extensión de nombre de archivo y aplicar las etiquetas a sólo ese tipo, o puede aplicar las etiquetas a un tipo de contenido existente (por ejemplo, "text"). El siguiente tutorial muestra cómo aplicar etiquetas para el tipo de contenido "text" la coincidencia de llaves.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de clasificador de editor. Asigne a la solución el nombre `BraceMatchingTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementar un etiquetador de coincidencia de llaves  
 Para obtener un efecto similar al que se usa en Visual Studio de resalte de llaves, puede implementar un etiquetador de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. El código siguiente muestra cómo definir el etiquetador para los pares de llaves en cualquier nivel de anidamiento. En este ejemplo, la llave de pares de []. [], y {} se definen en el constructor de etiquetador, pero en una implementación del lenguaje completa se definirían los pares de llaves pertinente en la especificación del lenguaje.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Para implementar un etiquetador de coincidencia de llaves  
  
1.  Agregue un archivo de clase y asígnele el nombre coincidencia de llaves.  
  
2.  Importe los siguientes espacios de nombres.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3.  Defina una clase `BraceMatchingTagger` que herede de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4.  Agregue las propiedades de la vista de texto, el búfer de origen y el punto de la instantánea actual y un conjunto de pares de llaves.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5.  En el constructor etiquetador, establezca las propiedades y suscribirse a los eventos de cambio de vista <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> y <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. En este ejemplo, con fines ilustrativos, también se definen los pares coincidentes en el constructor.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6.  Como parte de la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementación, declarar un evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7.  La posición del símbolo de intercalación actual de actualización de los controladores de eventos el `CurrentChar` propiedad y generar el evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> llaves de método para que coincidan con cualquiera, cuando el carácter actual es una llave de apertura o cuando el carácter anterior es una llave de cierre, al igual que en Visual Studio. Cuando se encuentra la coincidencia, este método crea una instancia de dos etiquetas, uno para la llave de apertura y otro para la llave de cierre.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Los siguientes métodos privados encuentra la llave correspondiente en cualquier nivel de anidamiento. El primer método busca el carácter de cierre que coincida con el carácter abierto:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. El siguiente método auxiliar busca el carácter abierto que coincide con un carácter de cierre:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementar un proveedor del etiquetador de coincidencia de llaves  
 Además de implementar un etiquetador, también debe implementar y exportar un proveedor del etiquetador. En este caso, el tipo del proveedor de contenido es "text". Esto significa que la coincidencia de llaves aparecerá en todos los tipos de archivos de texto, pero una implementación completa se aplicaría solo a un tipo de contenido específico de la coincidencia de llaves.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Para implementar un proveedor del etiquetador de llave coincidente  
  
1.  Declarar un proveedor del etiquetador que hereda de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, asígnele el nombre BraceMatchingTaggerProvider y expórtela con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> método para crear instancias de un BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución BraceMatchingTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Para compilar y probar soluciones BraceMatchingTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto que incluye llaves coincidentes.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Al colocar el símbolo de intercalación antes de una llave de apertura, debe aparecer resaltada dicha llave y la llave de cierre correspondiente. Al colocar el cursor justo después de la llave de cierre, debe aparecer resaltada dicha llave y la llave de apertura correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Vinculación de un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
