---
title: 'Tutorial: Esquema de esquematización de esquematización de esquematización de esquema Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697214"
---
# <a name="walkthrough-outlining"></a>Tutorial: Esquematización
Configure características basadas en lenguaje, como la esquematización, definiendo los tipos de regiones de texto que desea expandir o contraer. Puede definir regiones en el contexto de un servicio de lenguaje, o definir su propia extensión de nombre de archivo y tipo de contenido y aplicar la definición de región solo a ese tipo, o aplicar las definiciones de región a un tipo de contenido existente (por ejemplo, "texto"). En este tutorial se muestra cómo definir y mostrar regiones de esquematización.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Crear un proyecto de VSIX. Asigne a la solución el nombre `OutlineRegionTest`.

2. Agregue una plantilla de elemento Clasificador de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

## <a name="implement-an-outlining-tagger"></a>Implementar un etiquetadero de esquematización
 Las regiones de esquematización<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>están marcadas por un tipo de etiqueta ( ). Esta etiqueta proporciona el comportamiento de esquematización estándar. La región delineada se puede expandir o contraer. La región delineada está marcada**+** por un signo Más ( )**-** si está contraída o un signo Menos ( ) si se expande y la región expandida está demarcada por una línea vertical.

 Los pasos siguientes muestran cómo definir un etiquetador que crea regiones de esquematización para todas las regiones delimitadas por los corchetes (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Para implementar un tagger de esquematización

1. Agregue un archivo de clase y asígnele el nombre `OutliningTagger`.

2. Importe los siguientes espacios de nombres.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Cree una `OutliningTagger`clase denominada y <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>haga que implemente:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Agregue algunos campos para realizar un seguimiento del búfer de texto y la instantánea y para acumular los conjuntos de líneas que se deben etiquetar como regiones de esquematización. Este código incluye una lista de regiones objetos (que se definirán más adelante) que representan las regiones de esquematización.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Agregue un constructor de etiqueta que inicialice los campos, analice el <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> búfer y agregue un controlador de eventos al evento.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> el método, que crea una instancia de los intervalos de etiquetas. En este ejemplo se supone <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> que los intervalos de los pasados al método son contiguos, aunque no siempre puede ser el caso. Este método crea una instancia de un nuevo intervalo de etiquetas para cada una de las regiones de esquematización.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Declare `TagsChanged` un controlador de eventos.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Agregue `BufferChanged` un controlador de <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos que responda a eventos analizando el búfer de texto.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Agregue un método que analice el búfer. El ejemplo que se muestra aquí es solo para la ilustración. Analiza sincrónicamente el búfer en regiones de esquematización anidadas.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. El siguiente método auxiliar obtiene un entero que representa el nivel de la esquematización, de forma que 1 es el par de llaves más a la izquierda.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. El siguiente método auxiliar traduce una región (definida más adelante en este artículo) en un SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. El código siguiente es solo para la ilustración. Define una clase PartialRegion que contiene el número de línea y el desplazamiento del inicio de una región de esquematización y una referencia a la región primaria (si existe). Este código permite al analizador configurar regiones de esquematización anidadas. Una clase Region derivada contiene una referencia al número de línea del final de una región de esquematización.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementar un proveedor de etiquetas
 Exporte un proveedor de etiquetas para su etiqueta. El proveedor de `OutliningTagger` etiquetado crea un búfer para un búfer del `OutliningTagger` tipo de contenido "text" o, de lo contrario, devuelve un si el búfer ya tiene uno.

### <a name="to-implement-a-tagger-provider"></a>Para implementar un proveedor de etiquetas

1. Cree una `OutliningTaggerProvider` clase denominada <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>que implemente y expórtela con los atributos ContentType y TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> el método `OutliningTagger` agregando un a las propiedades del búfer.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Compile y pruebe el código
 Para probar este código, compile la solución OutlineRegionTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para compilar y probar la solución OutlineRegionTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Crear un archivo de texto Escriba algún texto que incluya tanto los corchetes de apertura como los corchetes de cierre.

    ```
    [
       Hello
    ]
    ```

4. Debe haber una región de esquematización que incluya ambos corchetes. Debería poder hacer clic en el signo menos a la izquierda del corchete abierto para contraer la región de esquematización. Cuando la región está contraída, el símbolo de puntos suspensivos (*...*) debe aparecer a la izquierda de la región contraída y debe aparecer una ventana emergente que contiene el **texto de desplazamiento** del texto al mover el puntero sobre los puntos suspensivos.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
