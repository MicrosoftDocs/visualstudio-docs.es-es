---
title: 'Tutorial: esquematización | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb338803d50b2ecc9af8c8db6a6b6dc2f3631161
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906184"
---
# <a name="walkthrough-outlining"></a>Tutorial: Esquematización
Configure características basadas en lenguajes como la esquematización definiendo los tipos de regiones de texto que desea expandir o contraer. Puede definir regiones en el contexto de un servicio de lenguaje o definir su propia extensión de nombre de archivo y tipo de contenido, y aplicar la definición de región solo a ese tipo o aplicar las definiciones de región a un tipo de contenido existente (como "texto"). En este tutorial se muestra cómo definir y mostrar las regiones de esquematización.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Crear un proyecto de VSIX. Asigne a la solución el nombre `OutlineRegionTest`.

2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

## <a name="implement-an-outlining-tagger"></a>Implementar un etiquetador de esquematización
 Las regiones de esquematización se marcan con un tipo de etiqueta ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Esta etiqueta proporciona el comportamiento de esquematización estándar. La región esquematizada se puede expandir o contraer. La región esquematizada se marca con un signo más ( **+** ) si está contraído o un signo menos ( **-** ) si se expande, y la región expandida está delimitada por una línea vertical.

 En los pasos siguientes se muestra cómo definir un etiquetador que crea regiones de esquematización para todas las regiones delimitadas por los corchetes (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Para implementar un etiquetador de esquematización

1. Agregue un archivo de clase y asígnele el nombre `OutliningTagger`.

2. Importe los siguientes espacios de nombres.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Cree una clase denominada `OutliningTagger` y haga que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Agregue algunos campos para realizar el seguimiento del búfer de texto y de la instantánea, y para acumular los conjuntos de líneas que se deben etiquetar como regiones de esquematización. Este código incluye una lista de objetos region (que se definirán más adelante) que representan las regiones de esquematización.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Agregue un constructor de etiquetador que inicialice los campos, analice el búfer y agregue un controlador de eventos al <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método, que crea instancias de los intervalos de etiquetas. En este ejemplo se da por supuesto que los intervalos del <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> pasado en el método son contiguos, aunque puede que no siempre sea el caso. Este método crea una instancia de un nuevo intervalo de etiquetas para cada una de las regiones de esquematización.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Declare un `TagsChanged` controlador de eventos.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Agregue un `BufferChanged` controlador de eventos que responda a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> los eventos analizando el búfer de texto.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Agregue un método que analice el búfer. Aquí solo se muestra el ejemplo. Analiza sincrónicamente el búfer en regiones de esquematización anidadas.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. El siguiente método auxiliar obtiene un entero que representa el nivel de la esquematización, de modo que 1 es el par de llave más a la izquierda.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. El método auxiliar siguiente traduce una región (que se define más adelante en este artículo) a SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. El código siguiente solo es para fines ilustrativos. Define una clase PartialRegion que contiene el número de línea y el desplazamiento del inicio de una región de esquematización, y una referencia a la región primaria (si existe). Este código permite al analizador configurar regiones de esquematización anidadas. Una clase de región derivada contiene una referencia al número de línea del final de una región de esquematización.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementar un proveedor de etiquetadores
 Exporte un proveedor de etiquetadores para el etiquetador. El proveedor del etiquetador crea un `OutliningTagger` para un búfer del tipo de contenido "Text", o bien devuelve un `OutliningTagger` si el búfer ya tiene uno.

### <a name="to-implement-a-tagger-provider"></a>Para implementar un proveedor de etiquetadores

1. Cree una clase denominada `OutliningTaggerProvider` que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> y expórtelos con los atributos ContentType y TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método agregando `OutliningTagger` a las propiedades del búfer.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución OutlineRegionTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para compilar y probar la solución OutlineRegionTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Crear un archivo de texto Escriba algún texto que incluya los corchetes de apertura y los corchetes de cierre.

    ```
    [
       Hello
    ]
    ```

4. Debe haber una región de esquematización que incluya ambos corchetes. Debe poder hacer clic en el signo menos situado a la izquierda del corchete de apertura para contraer la región de esquematización. Cuando se contrae la región, el símbolo de puntos suspensivos (*...*) debe aparecer a la izquierda de la región contraída y debe aparecer un elemento emergente que contiene el **texto de desplazamiento** del texto cuando se mueve el puntero sobre los puntos suspensivos.

## <a name="see-also"></a>Vea también
- [Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
