---
title: 'Tutorial: Esquematización | Microsoft Docs'
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
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6737d9fffa1f0f38fab57edd4031647d0cc1510e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578709"
---
# <a name="walkthrough-outlining"></a>Tutorial: Esquematización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Tutorial: esquematización](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-outlining).  
  
Puede implementar características basadas en lenguaje como mediante la definición de los tipos de regiones de texto que desea expandir o contraer la esquematización. Puede definir regiones en el contexto de un servicio de lenguaje, o puede definir su propio tipo de contenido y la extensión de nombre de archivo y la definición de la región se aplican sólo a ese tipo, o puede aplicar las definiciones de la región a un tipo de contenido existente (por ejemplo, "text"). En este tutorial se muestra cómo definir y mostrar las regiones de esquematización.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto VSIX. Nombre de la solución `OutlineRegionTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementar un etiquetador de esquematización  
 Las regiones de esquematización se marcan con un tipo de etiqueta (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Esta etiqueta proporciona el estándar de comportamiento de esquematización. Puede expandir o contraer la región esquematizada. La región esquematizada está marcada por un signo más, si está contraído o un signo menos si se expande y la región expandida es enmarcado por una línea vertical.  
  
 Los pasos siguientes muestran cómo definir un etiquetador que crea las regiones de esquematización para todas las regiones que están delimitadas por "[" y "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Para implementar un etiquetador de esquematización  
  
1.  Agregue un archivo de clase y asígnele el nombre `OutliningTagger`.  
  
2.  Importe los siguientes espacios de nombres.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  Cree una clase denominada `OutliningTagger`, y hacer que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  Agregue algunos campos para realizar un seguimiento del búfer de texto y la instantánea y acumular los conjuntos de líneas que se deben etiquetar como las regiones de esquematización. Este código incluye una lista de objetos de región (que se define más adelante) que representan las regiones de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  Agregue un constructor de etiquetador que inicializa los campos, analiza el búfer y se agrega un controlador de eventos para el <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> abarca el método, que crea una instancia de la etiqueta. En este ejemplo se da por supuesto que los intervalos en el <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> pasado al método son contiguas, aunque esto no sea siempre el caso. Este método crea una instancia de un nuevo intervalo de etiqueta para cada una de las regiones de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  Declarar un `TagsChanged` controlador de eventos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  Agregar un `BufferChanged` controlador de eventos que responde a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos analizando el búfer de texto.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Agregue un método que analiza el búfer. El ejemplo presentado aquí tiene solo fines ilustrativos. Analiza el búfer en las regiones de esquematización anidadas sincrónicamente.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. El siguiente método auxiliar Obtiene un entero que representa el nivel de la esquematización, tal que 1 es el par de llaves más a la izquierda.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. El siguiente método auxiliar traduce una región (definida más adelante en este tema) en un elemento SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. El código siguiente es únicamente con fines ilustrativos. Define una clase PartialRegion que contiene el número de línea y el desplazamiento del inicio de una región de esquematización y también una referencia a la región primaria (si existe). Esto permite que el analizador configurar anidar las regiones de esquematización. Una clase derivada de la región contiene una referencia al número de línea del final de una región de esquematización.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementar un proveedor del etiquetador  
 Debe exportar un proveedor del etiquetador para el etiquetador. El proveedor del etiquetador crea un `OutliningTagger` para un búfer del tipo de contenido "text", o se devuelve otra una `OutliningTagger` si el búfer ya tiene uno.  
  
#### <a name="to-implement-a-tagger-provider"></a>Para implementar un proveedor del etiquetador  
  
1.  Cree una clase denominada `OutliningTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>y expórtelo con los atributos ContentType y TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método agregando un `OutliningTagger` a las propiedades del búfer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
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
  
4.  Debe haber una región de esquematización que incluye dos llaves. Debe ser capaz de hacer clic en el signo menos a la izquierda de la llave de apertura para contraer la región de esquematización. Cuando la región se contrae, el símbolo de puntos suspensivos (...) debe aparecer a la izquierda de la región contraída y un menú emergente que contiene el texto **mantenga el puntero de texto** debe aparecer al mover el puntero sobre los puntos suspensivos.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

