---
title: Proporcionar información empaquetado e implementación de elementos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 078715380bb5ddc570d745d76fabe4d8a264eef0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Proporcionar información de empaquetado e implementación en los elementos del proyecto
  Todos los elementos de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tienen propiedades que puede usar para proporcionar datos adicionales cuando el proyecto se implementa en SharePoint. Estas propiedades son las siguientes:  
  
-   Propiedades de características  
  
-   Receptores de características  
  
-   Referencias de salida del proyecto  
  
-   Entradas de controles seguros  
  
 Estas propiedades aparecen en la **propiedades** ventana.  
  
## <a name="feature-properties"></a>Propiedades de características  
 Use la **Feature Properties** propiedad para especificar los datos que utiliza la característica. Datos de propiedades de características están un conjunto de valores (almacenados como pares clave-valor) que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada la característica, se puede obtener acceso a los valores de propiedad en el código.  
  
 Cuando se agrega un valor de propiedad de característica a un elemento de proyecto, el valor se agrega como un elemento en el manifiesto de la característica del elemento. En un proyecto de modelo de conectividad de datos profesionales (BDC), por ejemplo, la propiedad de característica ModelFileName aparece como:  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Después de establecer un valor de propiedad de la característica, se agrega como un FeatureProperty (elemento) en el archivo del proyecto .spdata. Para obtener información acerca del acceso a las propiedades de SharePoint, vea [SPFeaturePropertyCollection Class](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Los valores de propiedad de característica idénticos de todos los elementos de proyecto se combinan en el manifiesto de la característica. Sin embargo, si dos elementos del proyecto especifican la misma clave de propiedad de característica con valores no coincidentes, se produce un error de validación.  
  
 Para agregar propiedades de característica directamente al archivo de características (* .feature), llame a la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] método del modelo de objetos de SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Si utiliza este método, tenga en cuenta que la misma regla acerca de cómo agregar valores de propiedad de característica idénticos en Feature Properties también se aplica a propiedades que se agregan directamente al archivo de características.  
  
## <a name="feature-receiver"></a>Receptor de características  
 Receptores de características son código que se ejecuta cuando se producen determinados eventos con un elemento de proyecto que contiene la característica. Por ejemplo, puede definir receptores de características que se ejecutan cuando se instala, se activa o se actualiza la característica. Una manera de agregar un receptor de características consiste en agregar directamente a una característica como se describe en [Tutorial: Agregar receptores de eventos de características](../sharepoint/walkthrough-add-feature-event-receivers.md). Otra forma consiste en hacer referencia a un nombre de clase de receptor de características y el ensamblado en el **receptor de características** propiedad.  
  
### <a name="direct-method"></a>Método directo  
 Al agregar un receptor de características a una característica directamente, se coloca un archivo de código en el **característica** nodo en el Explorador de soluciones. Al compilar la solución de SharePoint, el código se compila en un ensamblado e implementa en SharePoint. De forma predeterminada, las propiedades de características **ensamblado del receptor** y **clase del receptor de** hacer referencia al nombre de clase y el ensamblado.  
  
### <a name="reference-method"></a>Reference (método)  
 Otra manera de agregar un receptor de características es mediante el uso de la **receptor de características** propiedad de un elemento de proyecto para hacer referencia a un ensamblado del receptor de características. El valor de propiedad de receptor de características tiene dos subpropiedades: **ensamblado** y **nombre de la clase**. El ensamblado debe usar su completo, el nombre "seguro" y el nombre de clase deben ser el nombre de tipo completo. Para más información, vea [Ensamblados con nombre seguro](http://go.microsoft.com/fwlink/?LinkID=169573). Después de implementar la solución en SharePoint, la característica usa el receptor de características que se hace referencia para controlar los eventos de característica.  
  
 En tiempo de compilación de soluciones, los valores de propiedad de receptor de características en la característica y sus proyectos combinan juntas para establecer los atributos ReceiverAssembly y ReceiverClass del elemento de característica en el manifiesto de la característica del archivo de solución (.wsp) de SharePoint. Por lo tanto, si se especifican los valores de propiedad de ensamblado y el nombre de clase de un elemento de proyecto y una característica, deben coincidir los valores de propiedad de característica y elemento de proyecto. Si los valores no coinciden, recibirá un error de validación. Si desea que un elemento de proyecto para hacer referencia a un ensamblado del receptor de características distinto del que utiliza la característica, muévalo a otra característica.  
  
 Si hace referencia a un ensamblado del receptor de características que ya no está en el servidor, también debe incluir el propio archivo de ensamblado en el paquete; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no lo agrega automáticamente. Cuando se implementa la característica, se copia el archivo de ensamblado para que el sistema [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] o la carpeta Bin en el directorio físico de SharePoint. Para obtener más información, vea Cómo: [Cómo: agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Para obtener más información acerca de los receptores de características, vea [receptor de eventos de características](http://go.microsoft.com/fwlink/?LinkID=169574) y [eventos de la función](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Referencias de salida del proyecto  
 La propiedad Project Output References especifica una dependencia, como un ensamblado, que el elemento de proyecto necesita ejecutar. Por ejemplo, suponga que su solución tiene un proyecto BDC y un proyecto de clase. Si el proyecto BDC tiene una dependencia en el ensamblado que se genera el proyecto de clase, puede hacer referencia al ensamblado en la propiedad de referencias de salida del proyecto del proyecto BDC. Cuando se empaqueta el proyecto de BDC, el ensamblado dependiente se incluye en el paquete.  
  
 Referencias de salida del proyecto normalmente son ensamblados, pero en algunos casos (por ejemplo, proyectos de Silverlight) pueden ser otros tipos de archivo.  
  
 Para obtener más información, consulte [Cómo: agregar una referencia de salida del proyecto](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Entradas de controles seguros  
 SharePoint proporciona un mecanismo de seguridad denominado entradas de controles seguros, para limitar el acceso de usuarios de confianza a ciertos controles. De forma predeterminada, SharePoint permite a los usuarios que no se confía cargar y crear páginas ASPX en el servidor de SharePoint. Para impedir que estos usuarios agreguen código no seguro a las páginas ASPX, SharePoint limita su acceso a *controles seguros*. Controles seguros son elementos Web designados como seguros y controles ASPX y que se puede utilizar cualquier usuario de su sitio. Para obtener más información, consulte [paso 4: agregar el elemento Web a la lista de controles seguros](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Cada elemento de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tiene una propiedad denominada **entradas de controles seguros** que tiene dos subpropiedades booleanas: **seguro** y **Safe Against Script**. La propiedad Safe especifica si los usuarios de confianza pueden tener acceso a un control. La propiedad Safe Against Script especifica si los usuarios de confianza pueden ver y cambiar las propiedades de un control.  
  
 Entradas de controles seguros se hace referencia por un ensamblado. Agregar entradas de controles seguros a un ensamblado del proyecto especificándolas en el elemento de proyecto **entradas de controles seguros** propiedad. Sin embargo, también puede agregar entradas de controles seguros al ensamblado del proyecto a través de la **avanzadas** pestaña en el **Diseñador de paquetes** cuando se agrega un ensamblado adicional al paquete. Para obtener más información, consulte [Cómo: marcar los controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md) o [registrar un ensamblado de elemento Web como un Control seguro](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Entradas XML para controles seguros  
 Cuando se agrega una entrada de control seguro a un elemento de proyecto o al ensamblado del proyecto, se escribe una referencia en el manifiesto del paquete en el formato siguiente:  
  
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
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extender el empaquetado y la implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  