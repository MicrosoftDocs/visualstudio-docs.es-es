---
title: 'Tutorial: esquematización | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201955"
---
# <a name="walkthrough-outlining"></a>Tutorial: Esquematización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar características basadas en lenguajes como la esquematización definiendo los tipos de regiones de texto que desea expandir o contraer. Puede definir regiones en el contexto de un servicio de lenguaje, o bien puede definir su propia extensión de nombre de archivo y tipo de contenido, y aplicar la definición de región solo a ese tipo, o bien puede aplicar las definiciones de región a un tipo de contenido existente (como "texto"). En este tutorial se muestra cómo definir y mostrar las regiones de esquematización.  
  
## <a name="prerequisites"></a>Prerrequisitos  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1. Cree un proyecto de VSIX. Asigne a la solución el nombre `OutlineRegionTest`.  
  
2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Elimine los archivos de clase existentes.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementar un etiquetador de esquematización  
 Las regiones de esquematización se marcan con un tipo de etiqueta ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Esta etiqueta proporciona el comportamiento de esquematización estándar. La región esquematizada se puede expandir o contraer. La región esquematizada se marca con un signo más si está contraído o un signo menos si se expande, y la región expandida se delimita mediante una línea vertical.  
  
 En los pasos siguientes se muestra cómo definir un etiquetador que crea regiones de esquematización para todas las regiones que están delimitadas por "[" y "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Para implementar un etiquetador de esquematización  
  
1. Agregue un archivo de clase y asígnele el nombre `OutliningTagger`.  
  
2. Importe los siguientes espacios de nombres.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Cree una clase denominada `OutliningTagger` y haga que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Agregue algunos campos para realizar el seguimiento del búfer de texto y de la instantánea, y para acumular los conjuntos de líneas que se deben etiquetar como regiones de esquematización. Este código incluye una lista de objetos region (que se definirán más adelante) que representan las regiones de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Agregue un constructor de etiquetador que inicialice los campos, analice el búfer y agregue un controlador de eventos al <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método, que crea instancias de los intervalos de etiquetas. En este ejemplo se da por supuesto que los intervalos del <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> pasado en el método son contiguos, aunque este no siempre es el caso. Este método crea una instancia de un nuevo intervalo de etiquetas para cada una de las regiones de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Declare un `TagsChanged` controlador de eventos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Agregue un `BufferChanged` controlador de eventos que responda a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> los eventos analizando el búfer de texto.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Agregue un método que analice el búfer. Aquí solo se muestra el ejemplo. Analiza sincrónicamente el búfer en regiones de esquematización anidadas.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. El siguiente método auxiliar obtiene un entero que representa el nivel de la esquematización, de modo que 1 es el par de llave más a la izquierda.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. El método auxiliar siguiente traduce una región (que se define más adelante en este tema) a SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. El código siguiente solo es para fines ilustrativos. Define una clase PartialRegion que contiene el número de línea y el desplazamiento del inicio de una región de esquematización, además de una referencia a la región primaria (si existe). Esto permite al analizador configurar regiones de esquematización anidadas. Una clase de región derivada contiene una referencia al número de línea del final de una región de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementar un proveedor de etiquetadores  
 Debe exportar un proveedor de etiquetadores para el etiquetador. El proveedor del etiquetador crea un `OutliningTagger` para un búfer del tipo de contenido "Text", o bien devuelve un `OutliningTagger` si el búfer ya tiene uno.  
  
#### <a name="to-implement-a-tagger-provider"></a>Para implementar un proveedor de etiquetadores  
  
1. Cree una clase denominada `OutliningTaggerProvider` que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> y expórtelos con los atributos ContentType y TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método agregando `OutliningTagger` a las propiedades del búfer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución OutlineRegionTest y ejecútela en la instancia experimental.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para compilar y probar la solución OutlineRegionTest  
  
1. Compile la solución.  
  
2. Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3. Crear un archivo de texto Escriba algún texto que incluya la llave de apertura y la llave de cierre.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Debe haber una región de esquematización que incluya ambas llaves. Debe poder hacer clic en el signo menos situado a la izquierda de la llave de apertura para contraer la región de esquematización. Cuando se contrae la región, el símbolo de puntos suspensivos (...) debe aparecer a la izquierda de la región contraída y debe aparecer un elemento emergente que contiene el **texto de desplazamiento** del texto cuando se mueve el puntero sobre los puntos suspensivos.  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
