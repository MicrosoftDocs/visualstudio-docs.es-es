---
title: Managed Extensibility Framework en el editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702875"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework en el editor
El editor se compila mediante el uso de componentes de Managed Extensibility Framework (MEF). Puede compilar sus propios componentes de MEF para extender el editor y el código puede consumir también los componentes del editor.

## <a name="overview-of-the-managed-extensibility-framework"></a>Información general sobre el Managed Extensibility Framework
 MEF es una biblioteca de .NET que le permite agregar y modificar características de una aplicación o componente que sigue el modelo de programación de MEF. El editor de Visual Studio puede proporcionar y utilizar partes de componentes de MEF.

 MEF está incluido en el ensamblado de *System.ComponentModel.Composition.dll* de .NET Framework versión 4.

 Para obtener más información sobre MEF, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Componentes y contenedores de composición
 Una parte componente es una clase o un miembro de una clase que puede realizar una de las siguientes acciones (o ambas):

- Consumir otro componente

- Ser consumido por otro componente

  Por ejemplo, imagine una aplicación de compras que tenga un componente de entrada de pedidos que dependa de los datos de disponibilidad de productos proporcionados por un componente de inventario de almacén. En términos de MEF, la parte de inventario puede *exportar* los datos de disponibilidad del producto y la parte de la entrada de pedido puede *importar* los datos. La parte de entrada de pedidos y la parte de inventario no tienen que conocerse entre sí; el *contenedor de composición* (proporcionado por la aplicación host) es responsable de mantener el conjunto de exportaciones y de resolver las exportaciones e importaciones.

  Normalmente, el contenedor de composición <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> es propiedad del host. El contenedor de composición mantiene un *Catálogo* de componentes exportados.

### <a name="export-and-import-component-parts"></a>Exportar e importar partes de componentes
 Puede exportar cualquier funcionalidad, siempre que se implemente como una clase pública o un miembro público de una clase (propiedad o método). No tiene que derivar la parte de componente de <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . En su lugar, debe agregar un <xref:System.ComponentModel.Composition.ExportAttribute> atributo a la clase o al miembro de clase que desea exportar. Este atributo especifica el *contrato* por el que otra parte del componente puede importar su funcionalidad.

### <a name="the-export-contract"></a>El contrato de exportación
 <xref:System.ComponentModel.Composition.ExportAttribute>Define la entidad (clase, interfaz o estructura) que se está exportando. Normalmente, el atributo export toma un parámetro que especifica el tipo de la exportación.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 De forma predeterminada, el <xref:System.ComponentModel.Composition.ExportAttribute> atributo define un contrato que es el tipo de la clase de exportación.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 En el ejemplo, el `[Export]` atributo predeterminado es equivalente a `[Export(typeof(TestAdornmentLayerDefinition))]` .

 También puede exportar una propiedad o un método, como se muestra en el ejemplo siguiente.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importar una exportación de MEF
 Si desea consumir una exportación de MEF, debe conocer el contrato (normalmente, el tipo) por el que se exportó y agregar un <xref:System.ComponentModel.Composition.ImportAttribute> atributo que tenga ese valor. De forma predeterminada, el atributo import toma un parámetro, que es el tipo de la clase que modifica. Las siguientes líneas de código importan el <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Obtener la funcionalidad del editor de una parte del componente MEF
 Si el código existente es una parte del componente de MEF, puede usar los metadatos de MEF para consumir partes del componente de editor.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Para consumir la funcionalidad del editor desde una parte del componente MEF

1. Agregue referencias a *System.Composition.ComponentModel.dll*, que se encuentra en la caché de ensamblados global (GAC) y en los ensamblados del editor.

2. Agregue las directivas Using pertinentes.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Agregue el `[Import]` atributo a la interfaz de servicio, como se indica a continuación.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Una vez obtenido el servicio, puede utilizar cualquiera de sus componentes.

5. Cuando haya compilado el ensamblado, colóquelo en el *.. \* Carpeta \Common7\IDE\Components de la instalación de Visual Studio.

## <a name="see-also"></a>Vea también
- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
