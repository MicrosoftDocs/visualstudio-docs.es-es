---
title: Managed Extensibility Framework en el Editor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4677b10d54a6c591c2f60e4c0b1f2978ad49a0ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework en el Editor
El editor se compila mediante componentes de Managed Extensibility Framework (MEF). Puede crear sus propios componentes MEF para ampliar el editor y el código puede consumir los componentes del editor.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Información general sobre Managed Extensibility Framework  
 MEF es una biblioteca de .NET que le permite agregar y modificar las características de una aplicación o componente que sigue el modelo de programación de MEF. El editor de Visual Studio puede proporcionar y consumir los componentes de MEF.  
  
 MEF se encuentra en el ensamblado de .NET Framework versión 4 System.ComponentModel.Composition.dll.  
  
 Para obtener más información acerca de MEF, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Componentes y contenedores de composición  
 Un componente es una clase o un miembro de una clase que puede realizar una (o ambas) de las siguientes acciones:  
  
-   Utilizar otro componente  
  
-   Ser utilizado por otro componente  
  
 Por ejemplo, considere una aplicación que tiene un componente de entrada de pedido que se base en datos de disponibilidad del producto proporcionadas por un componente de inventario de almacén de la compra. En términos MEF, la parte de inventario puede *exportar* datos de disponibilidad del producto y el elemento de entrada orden puede tener *importar* los datos. El elemento de entrada de pedido y la parte de inventario no es necesario saber entre sí; el *contenedor de composición* (proporcionado por la aplicación host) es responsable de mantener el conjunto de exportaciones y resolver las exportaciones e importa.  
  
 El contenedor de composición, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, normalmente es propiedad del host. El contenedor de composición mantiene un *catálogo* de componentes exportados.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportación e importación de componentes  
 Puede exportar cualquier funcionalidad, siempre y cuando se implementa como una clase pública o un miembro público de una clase (método o propiedad). No es necesario derivar su parte del componente de <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. En su lugar, debe agregar una <xref:System.ComponentModel.Composition.ExportAttribute> atributo a la clase o miembro de clase que se va a exportar. Este atributo especifica el *contrato* que otro componente parte puede importar su funcionalidad.  
  
### <a name="the-export-contract"></a>El contrato de exportación  
 El <xref:System.ComponentModel.Composition.ExportAttribute> define la entidad (clase, interfaz o estructura) que se va a exportar. Normalmente, el atributo de exportación toma un parámetro que especifica el tipo de la exportación.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 De forma predeterminada, la <xref:System.ComponentModel.Composition.ExportAttribute> atributo define un contrato que es el tipo de la clase de exportación.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 En el ejemplo, el valor predeterminado `[Export]` atributo es equivalente a `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 También puede exportar una propiedad o método, tal como se muestra en el ejemplo siguiente.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importar una exportación MEF  
 Si desea utilizar una exportación MEF, debe conocer el contrato (normalmente el tipo) por el que se exportó y agregar un <xref:System.ComponentModel.Composition.ImportAttribute> un atributo que tenga ese valor. De forma predeterminada, el atributo import toma un parámetro, que es el tipo de la clase que modifica. Las siguientes líneas de importación de código la <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Obtener la funcionalidad del Editor de un componente MEF  
 Si el código existente es un componente MEF, puede utilizar MEF metadatos para utilizar el editor de componentes.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Para utilizar la funcionalidad del editor de un componente MEF  
  
1.  Agregar referencias a System.Composition.ComponentModel.dll, que se encuentra en la caché global de ensamblados (GAC), y a los ensamblados de editor.  
  
2.  Agregar las correspondientes instrucciones de uso.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Agregar el `[Import]` atribuir a la interfaz de servicio, como se indica a continuación.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Cuando se ha obtenido el servicio, puede usar cualquiera de sus componentes.  
  
5.  Cuando se haya compilado el ensamblado, colocarlo en la.. Carpeta de \Common7\IDE\Components\ de la instalación de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)