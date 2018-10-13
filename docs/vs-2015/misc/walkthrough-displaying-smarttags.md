---
title: 'Tutorial: Mostrar etiquetas inteligentes | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: douge
ms.openlocfilehash: 84736e4cb4212b912d87caa7849a37bbc726ffdd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291023"
---
# <a name="walkthrough-displaying-smarttags"></a>Tutorial: Mostrar etiquetas inteligentes
Las etiquetas inteligentes están en desuso en beneficio de las bombillas. Vea [Walkthrough: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Las etiquetas inteligentes son etiquetas de texto que se expanden para mostrar un conjunto de acciones. Por ejemplo, en un proyecto de Visual Basic o Visual C#, aparece una línea roja debajo de una palabra cuando cambia el nombre de un identificador como un nombre de variable. Cuando mueve el puntero sobre el subrayado, se muestra un botón junto al puntero. Si hace clic en el botón, se muestra una acción sugerida, por ejemplo, **Cambiar nombre de IsRead a IsReady**. Si hace clic en la acción, todas las referencias a **IsRead** en el proyecto cambian su nombre a **IsReady**.  
  
 Aunque las etiquetas inteligentes son parte de la implementación de IntelliSense en el editor, puede implementar las etiquetas inteligentes mediante subclases de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> y, luego, mediante la implementación de la interfaz de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> y la interfaz de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.  
  
> [!NOTE]
>  Otros tipos de etiquetas pueden implementarse de forma similar.  
  
 El siguiente tutorial muestra cómo crear una etiqueta inteligente que aparece en la palabra actual y le sugiere dos acciones: **Convertir a mayúsculas** y **Convertir a minúsculas**.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de clasificador de editor. Asigne a la solución el nombre `SmartTagTest`.  
  
2.  Abra el archivo de manifiesto source.extension.vsix en el editor de manifiestos VSIX.  
  
3.  Asegúrese de que la sección **Activos** contiene un tipo `Microsoft.VisualStudio.MefComponent` , el **Origen** está establecido en `A project in current solution`y **Proyecto** está establecido en SmartTagTest.dll.  
  
4.  Guarde y cierre el archivo Source.extension.vsixmanifest.  
  
5.  Agregue la siguiente referencia al proyecto y establezca **CopyLocal** a `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Elimine los archivos de clase existentes.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementar un etiquetador para etiquetas inteligentes  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Para implementar un etiquetador para etiquetas inteligentes  
  
1.  Agregue un archivo de clase y asígnele el nombre `TestSmartTag`.  
  
2.  Agregue las siguientes importaciones:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3.  Cree una clase denominada `TestSmartTag` que herede de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4.  Agregue un constructor para esta clase que llame al constructor base con un <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, lo que hará que aparezca una línea azul en el primer carácter de una palabra. (Si usa <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, aparecerá una línea roja en el último carácter de la palabra).  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5.  Agregue una clase denominada `TestSmartTagger` que se herede de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> del tipo `TestSmartTag` e implemente <xref:System.IDisposable>.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6.  Agregue los campos privados siguientes a la clase de etiquetador.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7.  Agregue un constructor que establezca los campos privados y se suscriba al evento <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8.  Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> para que la etiqueta se cree para la palabra actual. (Este método también llama a un método privado `GetSmartTagActions`, que se explica más adelante).  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Agregue un método `GetSmartTagActions` para configurar las acciones de etiquetas inteligentes. Las acciones se implementan en pasos posteriores.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Declare el evento `SmartTagsChanged`.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implemente el controlador de eventos `OnLayoutChanged` para generar el evento `TagsChanged`, lo que hará que se llame a <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implemente el método <xref:System.IDisposable.Dispose%2A> para que se cancele la suscripción del evento <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementar el proveedor del etiquetador de etiquetas inteligentes  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Para implementar el proveedor del etiquetador de etiquetas inteligentes  
  
1.  Cree una clase denominada `TestSmartTagTaggerProvider` que herede de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Expórtela con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before="default" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2.  Importe el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> como una propiedad.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3.  Implemente el método <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementar acciones de etiquetas inteligentes  
  
#### <a name="to-implement-smart-tag-actions"></a>Para implementar acciones de etiquetas inteligentes  
  
1.  Cree dos clases, la primera llamada `UpperCaseSmartTagAction` y la segunda llamada `LowerCaseSmartTagAction`. Ambas clases implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
     [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
     [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
     [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
     [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
 Ambas clases son iguales, salvo que una llama a <xref:System.String.ToUpper%2A> y la otra llama a <xref:System.String.ToLower%2A>. Los siguientes pasos abarcan solo la clase de acción de mayúsculas, pero debe implementar ambas clases. Siga los pasos para implementar la acción de mayúsculas como un modelo para implementar la acción de minúsculas.  
  
1.  Declare un conjunto de campos privados.  
  
     [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
     [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
2.  Agregue un constructor que establezca los campos.  
  
     [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
     [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
3.  Implemente las propiedades de la siguiente manera:  
  
     [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
     [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
4.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> reemplazando el texto en el intervalo por su equivalente en mayúsculas.  
  
     [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
     [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución SmartTagTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Para compilar y probar la solución SmartTagTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto.  
  
     Debe aparecer una línea azul debajo de la primera letra de la primera palabra del texto.  
  
4.  Mueva el puntero sobre la línea azul.  
  
     Debe aparecer un botón junto al puntero.  
  
5.  Al hacer clic en el botón, deben aparecer dos acciones sugeridas: **Convertir a mayúsculas** y **Convertir a minúsculas**. Si hace clic en la primera acción, todo el texto de la palabra actual se debe convertir a mayúsculas. Si hace clic en la segunda acción, todo el texto de la palabra actual se debe convertir a minúsculas.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)