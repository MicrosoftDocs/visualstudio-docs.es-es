---
title: "Tutorial: Esquematización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 15dd5f0121fca86a38631bf775ec25d4428632e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-outlining"></a>Tutorial: esquematización
Puede implementar características basadas en lenguaje como mediante la definición de los tipos de regiones de texto que desea expandir o contraer la esquematización. Puede definir las regiones en el contexto de un servicio de lenguaje, puede definir su propio tipo de contenido y la extensión de nombre de archivo y la definición de la región se aplican sólo a ese tipo o puede aplicar las definiciones de la región a un tipo de contenido existente (por ejemplo, "text"). Este tutorial muestra cómo definir y mostrar las regiones de esquematización.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto VSIX. Llame a la solución `OutlineRegionTest`.  
  
2.  Agregar una plantilla de elementos de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementar un etiquetador esquematización  
 Regiones de esquematización se marcan con un tipo de etiqueta (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Esta etiqueta proporciona el estándar de comportamiento de esquematización. Puede expandir o contraer la región esquematizada. La región esquematizada se marca mediante un signo si está contraído o un signo menos si se expande y la región expandida es delimitada por una línea vertical.  
  
 Los pasos siguientes muestran cómo definir un etiquetador que crea regiones de esquematización para todas las regiones que están delimitadas por "[" y "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Para implementar un etiquetador esquematización  
  
1.  Agregue un archivo de clase y asígnele el nombre `OutliningTagger`.  
  
2.  Importe los siguientes espacios de nombres.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Cree una clase denominada `OutliningTagger`, y hacer que se implementan <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Agregue algunos campos que se va a realizar un seguimiento del búfer de texto y la instantánea como acumular los conjuntos de líneas que se deben etiquetar como regiones de esquematización. Este código incluye una lista de objetos de región (que se define más adelante) que representan las regiones de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Agregue un constructor de etiquetador que inicializa los campos, analiza el búfer y se agrega un controlador de eventos para el <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> abarca el método, que crea una instancia de la etiqueta. En este ejemplo se da por supuesto que los intervalos en la <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> pasa al método son contiguas, aunque esto no sea siempre el caso. Este método crea un nuevo intervalo de etiqueta para cada una de las regiones de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Declarar un `TagsChanged` controlador de eventos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Agregar un `BufferChanged` controlador de eventos que responde a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos analizando el búfer de texto.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Agregue un método que analiza el búfer. El ejemplo presentado aquí es solo para fines ilustrativos. Sincrónicamente analiza el búfer en las regiones de esquematización anidadas.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. El siguiente método auxiliar Obtiene un entero que representa el nivel de la esquematización, tal que 1 es el par de llave izquierda.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. El siguiente método auxiliar traduce una región (definida más adelante en este tema) en un SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. El código siguiente es solo para fines ilustrativos. Define una clase PartialRegion que contiene el número de línea y el desplazamiento del inicio de una región de esquematización así como una referencia a la región principal (si existe). Esto permite que el analizador configurar anidar regiones de esquematización. Una clase derivada de la región contiene una referencia al número de línea del final de una región de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementar un proveedor del etiquetador  
 Debe exportar un proveedor del etiquetador para su etiquetador. El proveedor del etiquetador crea un `OutliningTagger` por un búfer del tipo de contenido "text" o else devuelve un `OutliningTagger` si el búfer ya tiene uno.  
  
#### <a name="to-implement-a-tagger-provider"></a>Para implementar un proveedor del etiquetador  
  
1.  Cree una clase denominada `OutliningTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>y se exporta con los atributos de tipo de contenido y el valor de TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método agregando un `OutliningTagger` a las propiedades del búfer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución OutlineRegionTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para compilar y probar la solución OutlineRegionTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Crear un archivo de texto Escriba algún texto que incluye la llave de apertura y la llave de cierre.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Debería haber una región de esquematización que incluye dos llaves. Puede hacer clic en el signo menos a la izquierda de la llave de apertura para contraer la región de esquematización. Cuando la región está contraído, el símbolo de puntos suspensivos (...) debe aparecer a la izquierda de la región contraída y un menú emergente que contiene el texto **al mantener el puntero de texto** debe aparecer al mover el puntero sobre los puntos suspensivos.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)