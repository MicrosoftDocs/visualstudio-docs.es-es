---
title: Proporcionar información de implementación en los elementos de proyecto de empaquetado e | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4b2bf1fc1b011b79fdd8123218a78ac91a14579b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62550506"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Proporcionar información de empaquetado e implementación de elementos de proyecto
  Todos los elementos de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tienen propiedades que puede usar para proporcionar datos adicionales cuando el proyecto se implementa en SharePoint. Estas propiedades son las siguientes:

- Propiedades de características

- Receptores de características

- Referencias de salida del proyecto

- Entradas de controles seguros

  Estas propiedades aparecen en la **propiedades** ventana.

## <a name="feature-properties"></a>Propiedades de características
 Use la **característica propiedades** propiedad para especificar los datos que usa la característica. Datos de las propiedades de característica están un conjunto de valores (almacenados como pares clave/valor) que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada la característica, se puede obtener acceso a los valores de propiedad en el código.

 Cuando se agrega un valor de propiedad de característica a un elemento de proyecto, el valor se agrega como un elemento en el manifiesto de la característica del elemento. En un proyecto de modelo de conectividad de datos profesionales (BDC), por ejemplo, la propiedad de característica ModelFileName aparece como:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Después de establecer un valor de propiedad de característica, se agrega como un FeatureProperty (elemento) en el proyecto *.spdata* archivo. Para obtener información sobre el acceso a las propiedades de SharePoint, vea [SPFeaturePropertyCollection Class](http://go.microsoft.com/fwlink/?LinkId=177391).

 Los valores de propiedad de característica idénticos en todos los elementos de proyecto se combinan en el manifiesto de la característica. Sin embargo, si dos elementos del proyecto especifican la misma clave de propiedad de la función con valores no coincidentes, se produce un error de validación.

 Para agregar propiedades de característica directamente al archivo de características (*.feature*), llame a la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] método del modelo de objetos de SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Si utiliza este método, tenga en cuenta que la misma regla acerca de cómo agregar valores de propiedad de característica idénticos en las propiedades de características también se aplica a las propiedades que se agregan directamente al archivo de características.

## <a name="feature-receiver"></a>Receptor de características
 Receptores de características son código que se ejecuta cuando se produzcan determinados eventos en un elemento de proyecto que contiene la característica. Por ejemplo, puede definir los receptores de características que se ejecutan cuando se instala, activa o actualiza la característica. Una forma de agregar un receptor de características consiste en agregarla directamente a una característica como se describe en [Tutorial: Agregar receptores de eventos de característica](../sharepoint/walkthrough-add-feature-event-receivers.md). Otra manera consiste en hacer referencia a un nombre de clase del receptor de características y un ensamblado en el **receptor de características** propiedad.

### <a name="direct-method"></a>Método directo
 Al agregar un receptor de características a una característica directamente, se coloca un archivo de código en el **característica** nodo en el Explorador de soluciones. Al compilar la solución de SharePoint, el código se compila en un ensamblado y se implementa en SharePoint. De forma predeterminada, las propiedades de la característica **ensamblado del receptor** y **clase del receptor** hacer referencia al nombre de clase y ensamblado.

### <a name="reference-method"></a>Reference (método)
 Otra forma de agregar un receptor de características está usando el **receptor de características** propiedad de un elemento de proyecto para hacer referencia a un ensamblado del receptor de características. El valor de propiedad de receptor de características tiene dos subpropiedades: **Ensamblado** y **nombre de la clase**. El ensamblado debe usar su nombre completo, el nombre "seguro" y el nombre de clase deben ser el nombre de tipo completo. Para más información, vea [Ensamblados con nombre seguro](http://go.microsoft.com/fwlink/?LinkID=169573). Después de implementar la solución en SharePoint, la función usa el receptor de características que se hace referencia para controlar los eventos de característica.

 Solución de valores de propiedad de receptor en la característica de tiempo, la característica de compilación y combinan sus proyectos para establecer los atributos ReceiverAssembly y ReceiverClass del elemento de característica en el manifiesto de la característica de la solución de SharePoint (*.wsp* ) archivo. Por lo tanto, si se especifican los valores de propiedad del ensamblado y el nombre de clase de un elemento de proyecto y una característica, deben coincidir los valores de propiedad de característica y elemento de proyecto. Si los valores no coinciden, recibirá un error de validación. Si desea que un elemento de proyecto para hacer referencia a un ensamblado del receptor de características que no sea el que utiliza la característica, muévalo a otra característica.

 Si hace referencia a un ensamblado del receptor de características que ya no está en el servidor, también debe incluir el propio archivo de ensamblado en el paquete; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no se agrega automáticamente. Al implementar la característica, se copia el archivo de ensamblado para que el sistema [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] o la carpeta Bin en el directorio físico de SharePoint. Para obtener más información, consulte Cómo: [Cómo: Agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Para obtener más información acerca de los receptores de características, consulte [receptor de eventos de característica](http://go.microsoft.com/fwlink/?LinkID=169574) y [eventos de característica](http://go.microsoft.com/fwlink/?LinkID=169575).

## <a name="project-output-references"></a>Referencias de salida del proyecto
 La propiedad Project Output References especifica una dependencia, como un ensamblado, que debe ejecutarse el elemento de proyecto. Por ejemplo, suponga que su solución tiene un proyecto BDC y un proyecto de clase. Si el proyecto de BDC tiene una dependencia en el ensamblado que se genera el proyecto de clase, puede hacer referencia al ensamblado en la propiedad de Project Output References del proyecto BDC. Cuando se empaqueta el proyecto de BDC, el ensamblado dependiente se incluye en el paquete.

 Referencias de salida del proyecto normalmente son ensamblados, pero en algunos casos (por ejemplo, los proyectos de Silverlight) pueden ser otros tipos de archivo.

 Para obtener más información, vea [Cómo: Agregar una referencia de salida del proyecto](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Entradas de control seguras
 SharePoint proporciona un mecanismo de seguridad denominado entradas de control seguras, para limitar el acceso de usuarios de confianza para determinados controles. Por diseño, SharePoint permite a los usuarios de confianza cargar y crear páginas ASPX en el servidor de SharePoint. Para evitar que estos usuarios agreguen código no seguro a las páginas ASPX, SharePoint limita su acceso a *controles seguros*. Controles seguros son controles ASPX y elementos Web designados como seguros y que se puede utilizar cualquier usuario en su sitio. Para obtener más información, consulte [paso 4: Agregar el elemento Web a la lista de controles seguros](http://go.microsoft.com/fwlink/?LinkID=171014).

 Cada elemento de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tiene una propiedad denominada **entradas de controles seguros** que tiene dos subpropiedades booleanas: **Seguro** y **protegido frente a scripts**. La propiedad Safe especifica si los usuarios de confianza pueden tener acceso a un control. La propiedad Safe Against Script especifica si los usuarios pueden ver y cambiar las propiedades de un control.

 Entradas de control seguras se hace referencia en cada ensamblado. Agregar entradas de controles seguros a un ensamblado del proyecto escribiendo en el elemento de proyecto **entradas de controles seguros** propiedad. Sin embargo, también puede agregar entradas de controles seguros a un ensamblado del proyecto a través de la **avanzadas** pestaña en el **Diseñador de paquetes** cuando agrega un ensamblado adicional al paquete. Para obtener más información, vea [Cómo: Marcar los controles como seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md) o [registrar un ensamblado de elemento Web como un Control seguro](http://go.microsoft.com/fwlink/?LinkID=171013).

### <a name="xml-entries-for-safe-controls"></a>Entradas XML para controles seguros
 Cuando se agrega una entrada de control segura para un elemento de proyecto o ensamblado del proyecto, se escribe una referencia en el manifiesto del paquete en el formato siguiente:

```xml
<Assemblies>
    <Assembly Location="<assembly name>.dll"
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>
        <SafeControls>
            <SafeControl Assembly="<assembly name>.dll" Namespace=
              "<SharePoint project name>" Safe="<true/false>"
                TypeName="<control name>"
                SafeAgainstScript="<true/false>" />
        </SafeControls>
    </Assembly>
</Assemblies>
```

## <a name="see-also"></a>Vea también
- [Paquete e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Ampliar la implementación y empaquetado de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
