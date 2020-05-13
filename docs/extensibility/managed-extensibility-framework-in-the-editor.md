---
title: Managed Extensibility Framework en el Editor ( Managed Extensibility Framework in the Editor) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702875"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework en el editor
El editor se crea mediante componentes de Managed Extensibility Framework (MEF). Puede crear sus propios componentes MEF para ampliar el editor, y el código también puede consumir componentes del editor.

## <a name="overview-of-the-managed-extensibility-framework"></a>Visión general del marco de extensibilidad administrada
 MeF es una biblioteca de .NET que le permite agregar y modificar características de una aplicación o componente que sigue el modelo de programación MEF. El editor de Visual Studio puede proporcionar y consumir componentes MEF.

 El MEF se encuentra en el ensamblado *System.ComponentModel.Composition.dll* de .NET Framework versión 4.

 Para obtener más información acerca de MEF, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Piezas de componentes y contenedores de composición
 Una parte de componente es una clase o un miembro de una clase que puede realizar una (o ambas) de las siguientes acciones:

- Consumir otro componente

- Ser consumido por otro componente

  Por ejemplo, considere una aplicación de compras que tiene un componente de entrada de pedido que depende de los datos de disponibilidad del producto proporcionados por un componente de inventario de almacén. En términos MEF, la parte de inventario puede *exportar* datos de disponibilidad de productos y la parte de entrada de pedido puede *importar* los datos. La parte de entrada de pedido y la pieza de inventario no tienen que conocerse entre sí; el contenedor de *composición* (proporcionado por la aplicación anfitriona) es responsable de mantener el conjunto de exportaciones y resolver las exportaciones e importaciones.

  El contenedor <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>de composición, , suele ser propiedad del host. El contenedor de composición mantiene un *catálogo* de componentes exportados.

### <a name="export-and-import-component-parts"></a>Exportar e importar componentes
 Puede exportar cualquier funcionalidad, siempre que se implemente como una clase pública o un miembro público de una clase (propiedad o método). No es necesario derivar la <xref:System.ComponentModel.Composition.Primitives.ComposablePart>parte del componente de . En su lugar, <xref:System.ComponentModel.Composition.ExportAttribute> debe agregar un atributo a la clase o miembro de clase que desea exportar. Este atributo especifica el *contrato* por el que otra parte del componente puede importar la funcionalidad.

### <a name="the-export-contract"></a>El contrato de exportación
 Define <xref:System.ComponentModel.Composition.ExportAttribute> la entidad (clase, interfaz o estructura) que se está exportando. Normalmente, el atributo export toma un parámetro que especifica el tipo de la exportación.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 De forma <xref:System.ComponentModel.Composition.ExportAttribute> predeterminada, el atributo define un contrato que es el tipo de la clase de exportación.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 En el ejemplo, `[Export]` el atributo `[Export(typeof(TestAdornmentLayerDefinition))]`predeterminado es equivalente a .

 También puede exportar una propiedad o un método, como se muestra en el ejemplo siguiente.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importar una exportación MEF
 Cuando desee consumir una exportación MEF, debe conocer el contrato (normalmente el <xref:System.ComponentModel.Composition.ImportAttribute> tipo) por el que se exportó y agregar un atributo que tenga ese valor. De forma predeterminada, el atributo import toma un parámetro, que es el tipo de la clase que modifica. Las siguientes líneas de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> código importan el tipo.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Obtenga la funcionalidad del editor a partir de una pieza de componente MEF
 Si el código existente es una pieza de componente MEF, puede utilizar metadatos MEF para consumir partes de componentes del editor.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Para consumir la funcionalidad del editor desde una pieza de componente MEF

1. Agregue referencias a *System.Composition.ComponentModel.dll*, que se encuentra en la caché global de ensamblados (GAC) y a los ensamblados del editor.

2. Agregue las directivas using relevantes.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Agregue `[Import]` el atributo a la interfaz de servicio, como se indica a continuación.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Cuando haya obtenido el servicio, puede consumir cualquiera de sus componentes.

5. Cuando haya compilado el ensamblado, colóquelo en *.. Carpeta de componentes\* de la instalación de Visual Studio.

## <a name="see-also"></a>Vea también
- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
