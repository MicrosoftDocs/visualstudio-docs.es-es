---
title: "Tutorial: Mostrar etiquetas inteligentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], nuevos: etiquetas inteligentes"
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Tutorial: Mostrar etiquetas inteligentes
Las etiquetas inteligentes están en desuso en beneficio de las bombillas. Vea [Tutorial: Mostrar sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Las etiquetas inteligentes son etiquetas de texto que se expanden para mostrar un conjunto de acciones. Por ejemplo, en un proyecto de Visual Basic o Visual C\#, aparece una línea roja debajo de una palabra cuando cambia el nombre de un identificador como un nombre de variable. Cuando mueve el puntero sobre el subrayado, se muestra un botón junto al puntero. Si hace clic en el botón, se muestra una acción sugerida, por ejemplo, **Cambiar nombre de IsRead a IsReady**. Si hace clic en la acción, todas las referencias a **IsRead** en el proyecto cambian su nombre a **IsReady**.  
  
 Aunque las etiquetas inteligentes son parte de la implementación de IntelliSense en el editor, puede implementar las etiquetas inteligentes mediante subclases de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> y, luego, mediante la implementación de la interfaz de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> y la interfaz de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.  
  
> [!NOTE]
>  Otros tipos de etiquetas pueden implementarse de forma similar.  
  
 El siguiente tutorial muestra cómo crear una etiqueta inteligente que aparece en la palabra actual y le sugiere dos acciones: **Convertir a mayúsculas** y **Convertir a minúsculas**.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el Visual Studio SDK. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Crear un proyecto de Managed Extensibility Framework \(MEF\)  
  
#### Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de clasificador de editor. Asigne a la solución el nombre `SmartTagTest`.  
  
2.  Abra el archivo de manifiesto source.extension.vsix en el editor de manifiestos VSIX.  
  
3.  Asegúrese de que la sección **Activos** contiene un tipo `Microsoft.VisualStudio.MefComponent`, el **Origen** está establecido en `A project in current solution` y **Proyecto** está establecido en SmartTagTest.dll.  
  
4.  Guarde y cierre el archivo Source.extension.vsixmanifest.  
  
5.  Agregue la siguiente referencia al proyecto y establezca **CopyLocal** a `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Elimine los archivos de clase existentes.  
  
## Implementar un etiquetador para etiquetas inteligentes  
  
#### Para implementar un etiquetador para etiquetas inteligentes  
  
1.  Agregue un archivo de clase y asígnele el nombre `TestSmartTag`.  
  
2.  Agregue las siguientes importaciones:  
  
     [!code-cs[VSSDKSmartTagTest#1](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_1.cs)]
     [!code-vb[VSSDKSmartTagTest#1](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_1.vb)]  
  
3.  Cree una clase denominada `TestSmartTag` que herede de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#2](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_2.cs)]
     [!code-vb[VSSDKSmartTagTest#2](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_2.vb)]  
  
4.  Agregue un constructor para esta clase que llame al constructor base con un <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, lo que hará que aparezca una línea azul en el primer carácter de una palabra. \(Si usa <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, aparecerá una línea roja en el último carácter de la palabra\).  
  
     [!code-cs[VSSDKSmartTagTest#3](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_3.cs)]
     [!code-vb[VSSDKSmartTagTest#3](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_3.vb)]  
  
5.  Agregue una clase denominada `TestSmartTagger` que se herede de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> del tipo `TestSmartTag` e implemente <xref:System.IDisposable>.  
  
     [!code-cs[VSSDKSmartTagTest#4](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_4.cs)]
     [!code-vb[VSSDKSmartTagTest#4](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_4.vb)]  
  
6.  Agregue los campos privados siguientes a la clase de etiquetador.  
  
     [!code-cs[VSSDKSmartTagTest#5](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_5.cs)]
     [!code-vb[VSSDKSmartTagTest#5](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_5.vb)]  
  
7.  Agregue un constructor que establezca los campos privados y se suscriba al evento <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-cs[VSSDKSmartTagTest#6](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_6.cs)]
     [!code-vb[VSSDKSmartTagTest#6](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_6.vb)]  
  
8.  Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> para que la etiqueta se cree para la palabra actual. \(Este método también llama a un método privado `GetSmartTagActions`, que se explica más adelante\).  
  
     [!code-cs[VSSDKSmartTagTest#7](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_7.cs)]
     [!code-vb[VSSDKSmartTagTest#7](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_7.vb)]  
  
9. Agregue un método `GetSmartTagActions` para configurar las acciones de etiquetas inteligentes. Las acciones se implementan en pasos posteriores.  
  
     [!code-cs[VSSDKSmartTagTest#8](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_8.cs)]
     [!code-vb[VSSDKSmartTagTest#8](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_8.vb)]  
  
10. Declare el evento `SmartTagsChanged`.  
  
     [!code-cs[VSSDKSmartTagTest#9](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_9.cs)]
     [!code-vb[VSSDKSmartTagTest#9](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_9.vb)]  
  
11. Implemente el controlador de eventos `OnLayoutChanged` para generar el evento `TagsChanged`, lo que hará que se llame a <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>.  
  
     [!code-cs[VSSDKSmartTagTest#10](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_10.cs)]
     [!code-vb[VSSDKSmartTagTest#10](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_10.vb)]  
  
12. Implemente el método <xref:System.IDisposable.Dispose%2A> para que se cancele la suscripción del evento <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-cs[VSSDKSmartTagTest#11](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_11.cs)]
     [!code-vb[VSSDKSmartTagTest#11](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_11.vb)]  
  
## Implementar el proveedor del etiquetador de etiquetas inteligentes  
  
#### Para implementar el proveedor del etiquetador de etiquetas inteligentes  
  
1.  Cree una clase denominada `TestSmartTagTaggerProvider` que herede de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Expórtela con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before\="default" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#12](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_12.cs)]
     [!code-vb[VSSDKSmartTagTest#12](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_12.vb)]  
  
2.  Importe el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> como una propiedad.  
  
     [!code-cs[VSSDKSmartTagTest#13](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_13.cs)]
     [!code-vb[VSSDKSmartTagTest#13](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_13.vb)]  
  
3.  Implemente el método <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>.  
  
     [!code-cs[VSSDKSmartTagTest#14](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_14.cs)]
     [!code-vb[VSSDKSmartTagTest#14](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_14.vb)]  
  
## Implementar acciones de etiquetas inteligentes  
  
#### Para implementar acciones de etiquetas inteligentes  
  
1.  Cree dos clases, la primera llamada `UpperCaseSmartTagAction` y la segunda llamada `LowerCaseSmartTagAction`. Ambas clases implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
     [!code-cs[VSSDKSmartTagTest#15](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_15.cs)]
     [!code-vb[VSSDKSmartTagTest#15](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_15.vb)]  
  
     [!code-cs[VSSDKSmartTagTest#16](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_16.cs)]
     [!code-vb[VSSDKSmartTagTest#16](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_16.vb)]  
  
 Ambas clases son iguales, salvo que una llama a <xref:System.String.ToUpper%2A> y la otra llama a <xref:System.String.ToLower%2A>. Los siguientes pasos abarcan solo la clase de acción de mayúsculas, pero debe implementar ambas clases. Siga los pasos para implementar la acción de mayúsculas como un modelo para implementar la acción de minúsculas.  
  
1.  Declare un conjunto de campos privados.  
  
     [!code-cs[VSSDKSmartTagTest#17](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_17.cs)]
     [!code-vb[VSSDKSmartTagTest#17](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_17.vb)]  
  
2.  Agregue un constructor que establezca los campos.  
  
     [!code-cs[VSSDKSmartTagTest#18](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_18.cs)]
     [!code-vb[VSSDKSmartTagTest#18](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_18.vb)]  
  
3.  Implemente las propiedades de la siguiente manera:  
  
     [!code-cs[VSSDKSmartTagTest#19](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_19.cs)]
     [!code-vb[VSSDKSmartTagTest#19](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_19.vb)]  
  
4.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> reemplazando el texto en el intervalo por su equivalente en mayúsculas.  
  
     [!code-cs[VSSDKSmartTagTest#20](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_20.cs)]
     [!code-vb[VSSDKSmartTagTest#20](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_20.vb)]  
  
## Compilar y probar el código  
 Para probar este código, compile la solución SmartTagTest y ejecútelo en la instancia experimental.  
  
#### Para compilar y probar la solución SmartTagTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto.  
  
     Debe aparecer una línea azul debajo de la primera letra de la primera palabra del texto.  
  
4.  Mueva el puntero sobre la línea azul.  
  
     Debe aparecer un botón junto al puntero.  
  
5.  Al hacer clic en el botón, deben aparecer dos acciones sugeridas: **Convertir a mayúsculas** y **Convertir a minúsculas**. Si hace clic en la primera acción, todo el texto de la palabra actual se debe convertir a mayúsculas. Si hace clic en la segunda acción, todo el texto de la palabra actual se debe convertir a minúsculas.  
  
## Vea también  
 [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)