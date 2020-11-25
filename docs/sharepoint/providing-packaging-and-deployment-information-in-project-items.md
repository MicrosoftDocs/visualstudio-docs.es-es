---
title: Empaquetar & la información de implementación en elementos de proyecto
description: Agregar datos de empaquetado e implementación en los elementos de proyecto de SharePoint mediante propiedades de características, receptores de características, referencias de salida del proyecto y entidades de control seguro.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f73d8727fb960cf519d368d928aa20cae38ae1a9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970476"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Inclusión de información de empaquetado e implementación en los elementos del proyecto
  Todos los elementos de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tienen propiedades que se pueden usar para proporcionar datos adicionales cuando el proyecto se implementa en SharePoint. Estas propiedades son las siguientes:

- Propiedades de características

- Receptores de características

- Referencias de salida del proyecto

- Entradas de controles seguros

  Estas propiedades aparecen en la ventana **propiedades** .

## <a name="feature-properties"></a>Propiedades de características
 Use la propiedad **propiedades de característica** para especificar los datos que utiliza la característica. Los datos de las propiedades de característica son un conjunto de valores (almacenados como pares clave-valor) que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada la característica, se puede obtener acceso a los valores de propiedad en el código.

 Cuando se agrega un valor de propiedad de característica a un elemento de proyecto, el valor se agrega como un elemento en el manifiesto de la característica del elemento. En un proyecto de modelo de conectividad a datos profesionales (BDC), por ejemplo, la propiedad de la característica ModelFileName aparece como:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Después de establecer un valor de propiedad de característica, se agrega como un elemento Featureproperty (en el archivo *. spdata* del proyecto. Para obtener información sobre cómo obtener acceso a las propiedades de SharePoint, consulte [clase SPFeaturePropertyCollection](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Los valores de propiedad de características idénticas de todos los elementos de proyecto se combinan en el manifiesto de la característica. Sin embargo, si dos elementos de proyecto diferentes especifican la misma clave de propiedad de característica con valores no coincidentes, se produce un error de validación.

 Para agregar propiedades de características directamente al archivo de características (*. Feature*), llame al [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] método del modelo de objetos de SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . Si usa este método, tenga en cuenta que la misma regla sobre la adición de valores de propiedad de características idénticas en las propiedades de características también se aplica a las propiedades que se agregan directamente al archivo de características.

## <a name="feature-receiver"></a>Receptor de características
 Los receptores de características son código que se ejecuta cuando se producen determinados eventos en la característica que contiene un elemento de proyecto. Por ejemplo, puede definir los receptores de características que se ejecutan cuando se instala, activa o actualiza la característica. Una manera de agregar un receptor de características es agregarlo directamente a una característica, tal como se describe en [Tutorial: agregar receptores de eventos de características](../sharepoint/walkthrough-add-feature-event-receivers.md). Otra manera es hacer referencia a un ensamblado y un nombre de clase del receptor de características en la propiedad **receptor de características** .

### <a name="direct-method"></a>Método directo
 Al agregar directamente un receptor de características a una característica, se coloca un archivo de código bajo el nodo de **características** en explorador de soluciones. Al compilar la solución de SharePoint, el código se compila en un ensamblado y se implementa en SharePoint. De forma predeterminada, las propiedades de la característica de **ensamblado de receptor** y de **clase de receptor** hacen referencia al nombre de clase y ensamblado.

### <a name="reference-method"></a>Reference (método)
 Otra manera de agregar un receptor de características es usar la propiedad **receptor de características** de un elemento de proyecto para hacer referencia a un ensamblado del receptor de características. El valor de propiedad del receptor de características tiene dos subpropiedades: nombre de **ensamblado** y de **clase**. El ensamblado debe utilizar su nombre completo "Strong" y el nombre de la clase debe ser el nombre de tipo completo. Para más información, vea [Ensamblados con nombre seguro](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Después de implementar la solución en SharePoint, la característica usa el receptor de características al que se hace referencia para controlar los eventos de características.

 En el momento de la compilación de la solución, los valores de propiedad del receptor de características de la característica y sus proyectos se combinan juntos para establecer los atributos ReceiverAssembly y ReceiverClass del elemento de característica en el manifiesto de la característica del archivo de solución de SharePoint (*. wsp*). Por consiguiente, si se especifican los valores de propiedad de ensamblado y nombre de clase de un elemento de proyecto y una característica, los valores de propiedades de elemento de proyecto y característica deben coincidir. Si los valores no coinciden, recibirá un error de validación. Si desea que un elemento de proyecto haga referencia a un ensamblado del receptor de características que no sea el que utiliza su característica, muévalo a otra característica.

 Si hace referencia a un ensamblado del receptor de características que aún no está en el servidor, también debe incluir el propio archivo de ensamblado en el paquete; no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] lo agrega. Al implementar la característica, el archivo de ensamblado se copia en la carpeta del sistema [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] o de la ubicación del directorio físico de SharePoint. Para obtener más información, vea cómo: [Agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Para obtener más información acerca de los receptores de características, consulte [características del receptor de eventos](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) y [características](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Referencias de salida del proyecto
 La propiedad referencias de resultados del proyecto especifica una dependencia, como un ensamblado, que el elemento de proyecto necesita para ejecutarse. Por ejemplo, supongamos que la solución tiene un proyecto de BDC y un proyecto de clase. Si el proyecto de BDC tiene una dependencia en el ensamblado generado por el proyecto de clase, puede hacer referencia al ensamblado en la propiedad referencias de salida del proyecto del proyecto BDC. Cuando el proyecto de BDC está empaquetado, el ensamblado dependiente se incluye en el paquete.

 Las referencias de salida del proyecto suelen ser ensamblados, pero en algunos casos (como los proyectos de Silverlight) pueden ser otros tipos de archivo.

 Para obtener más información, vea [Cómo: agregar una referencia de salida de proyecto](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Entradas de control seguras
 SharePoint proporciona un mecanismo de seguridad, denominado entradas de control seguras, para limitar el acceso de los usuarios que no son de confianza a determinados controles. Por diseño, SharePoint permite que los usuarios que no son de confianza carguen y creen páginas ASPX en el servidor de SharePoint. Para evitar que estos usuarios agreguen código no seguro a las páginas ASPX, SharePoint limita su acceso a *los controles seguros*. Los controles seguros son controles ASPX y elementos Web designados como seguros y que puede usar cualquier usuario de su sitio. Para obtener más información, vea [paso 4: agregar el elemento Web a la lista de controles seguros](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Cada elemento de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tiene una propiedad denominada **entradas de control seguras** que tiene dos subpropiedades booleanas: **Safe** y **Safe with script**. La propiedad Safe especifica si los usuarios que no son de confianza pueden tener acceso a un control. La propiedad Safe Against script especifica si los usuarios que no son de confianza pueden ver y cambiar las propiedades de un control.

 Se hace referencia a las entradas de control seguras en cada ensamblado. Para agregar entradas de control seguras al ensamblado de un proyecto, debe escribirlas en la propiedad **entradas de control seguras** del elemento de proyecto. Sin embargo, también puede Agregar entradas de control seguras al ensamblado de un proyecto a través de la pestaña **Opciones avanzadas** del **Diseñador de paquetes** al agregar un ensamblado adicional al paquete. Para obtener más información, vea [Cómo: marcar controles como seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md) o [registrar un ensamblado de elemento Web como un control seguro](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

### <a name="xml-entries-for-safe-controls"></a>Entradas XML para controles seguros
 Cuando se agrega una entrada de control segura a un elemento de proyecto o al ensamblado del proyecto, se escribe una referencia en el manifiesto del paquete con el siguiente formato:

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
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Uso de módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
