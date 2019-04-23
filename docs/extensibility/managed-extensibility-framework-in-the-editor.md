---
title: Managed Extensibility Framework en el Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 708d9c7e41a3be24f9eaf28d86da94d47b187a93
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054019"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework en el editor
El editor se compila mediante componentes de Managed Extensibility Framework (MEF). Puede crear sus propios componentes MEF para ampliar el editor y el código puede consumir los componentes del editor.

## <a name="overview-of-the-managed-extensibility-framework"></a>Información general de Managed Extensibility Framework
 MEF es una biblioteca de .NET que le permite agregar y modificar las características de una aplicación o componente que sigue el modelo de programación de MEF. El editor de Visual Studio puede proporcionar y consumir los componentes de MEF.

 MEF se encuentra en la versión 4 de .NET Framework *System.ComponentModel.Composition.dll* ensamblado.

 Para obtener más información acerca de MEF, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Componentes y contenedores de composición
 Una parte componente es una clase o un miembro de una clase que puede hacer una (o ambas) de las siguientes acciones:

- Usar otro componente

- Se ha consumido por otro componente

  Por ejemplo, considere una aplicación de la compra que tiene un componente de entrada de orden que depende de los datos de disponibilidad de producto proporcionados por un componente de inventario de almacén. En términos MEF, la parte del inventario puede *exportar* datos de disponibilidad de productos y la puede parte de entrada de orden *importar* los datos. La parte de la entrada de orden y la parte del inventario no tienen que saber acerca de los otros; el *contenedor de composición* (proporcionado por la aplicación host) es responsable de mantener el conjunto de exportaciones y resolver las exportaciones e importa.

  El contenedor de composición, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, normalmente es propiedad del host. El contenedor de composición mantiene un *catálogo* componentes exportados.

### <a name="export-and-import-component-parts"></a>Exportar e importar elementos de componente
 Puede exportar ninguna funcionalidad, siempre y cuando se implementa como una clase pública o un miembro público de una clase (método o propiedad). No es necesario derivar de la parte del componente de <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. En su lugar, debe agregar un <xref:System.ComponentModel.Composition.ExportAttribute> atributo a la clase o miembro de clase que desea exportar. Este atributo especifica el *contrato* qué otro componente parte puede importar su funcionalidad.

### <a name="the-export-contract"></a>El contrato de exportación
 El <xref:System.ComponentModel.Composition.ExportAttribute> define la entidad (clase, interfaz o estructura) que se va a exportar. Normalmente, el atributo export toma un parámetro que especifica el tipo de la exportación.

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

 En el ejemplo, el valor predeterminado `[Export]` es equivalente al atributo `[Export(typeof(TestAdornmentLayerDefinition))]`.

 También puede exportar una propiedad o método, tal como se muestra en el ejemplo siguiente.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importar una exportación MEF
 Cuando desea consumir una exportación MEF, debe conocer el contrato (normalmente el tipo) por el que se ha exportado y agregar un <xref:System.ComponentModel.Composition.ImportAttribute> atributo que tiene ese valor. De forma predeterminada, el atributo import toma un parámetro, que es el tipo de la clase que modifica. Las siguientes líneas de importación de código la <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Obtener la funcionalidad del editor de una parte del componente MEF
 Si el código existente es una parte del componente MEF, puede utilizar metadatos MEF para consumir los componentes del editor.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Para utilizar la funcionalidad del editor de un elemento de componente MEF

1. Agregue referencias a *System.Composition.ComponentModel.dll*, que se encuentra en la caché global de ensamblados (GAC) y a los ensamblados del editor.

2. Agregue la correspondiente mediante instrucciones.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Agregar el `[Import]` atributo a la interfaz de servicio, como se indica a continuación.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Cuando haya obtenido el servicio, puede consumir cualquiera de sus componentes.

5. Cuando se compila el ensamblado, colocarlo en el *... \Common7\IDE\Components\* carpeta de la instalación de Visual Studio.

## <a name="see-also"></a>Vea también
- [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)