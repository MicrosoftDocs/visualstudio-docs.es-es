---
title: "Inicialización de diseñador y configuración de metadatos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicialización de diseñador y configuración de metadatos
Manipulación de los atributos de metadatos y el filtro asociado a un diseñador o componente del diseñador proporciona un mecanismo para aplicaciones definir qué herramientas se utilizan un determinado diseñador para controlar diferentes <xref:System.Type>objetos (por ejemplo, las estructuras de datos, clases o entidades gráficas), cuando el diseñador está disponible, y cómo el IDE de Visual Studio está configurado para admitir el diseñador (para la instancia que **herramientas** categoría o la pestaña está disponible).</xref:System.Type>  
  
 El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona varios mecanismos para facilitar el control de la inicialización del diseñador o componente de diseñador y la manipulación de sus metadatos en un VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicializando la información de configuración y metadatos  
 Dado que se cargan a petición, VSPackages no puede cargar por la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno antes de la creación de instancias de un diseñador. Por lo tanto, VSPackages no puede usar el mecanismo estándar para configurar un diseñador o componente del diseñador en la creación, que es controlar una <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>eventos.</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> En su lugar, un paquete VSPackage implementa una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>interfaz y se registra para proporcionar las personalizaciones, se conocen como extensiones de superficie de diseño.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>Personalizar la inicialización  
 Personalización de un diseñador, un componente o una superficie del diseñador, implica:  
  
1.  Modificar los metadatos del diseñador y cambiando efectivamente cómo un determinado <xref:System.Type>se tiene acceso o se convierten.</xref:System.Type>  
  
     Esto se hace normalmente a través de la <xref:System.Drawing.Design.UITypeEditor>o <xref:System.ComponentModel.TypeConverter>mecanismos.</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     Por ejemplo, cuando <xref:System.Windows.Forms>-se inicializan en función de los diseñadores, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno modifica el <xref:System.Drawing.Design.UITypeEditor>para <xref:System.Web.UI.WebControls.Image>objetos utilizados con el diseñador para utilizar el Administrador de recursos para obtener los mapas de bits en lugar de con el sistema de archivos.</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  Integración con el entorno, por ejemplo, al suscribirse a eventos o la obtención de información de configuración del proyecto. Puede obtener información de configuración de proyecto y suscribirse a eventos mediante la obtención de la <xref:System.ComponentModel.Design.ITypeResolutionService>interfaz.</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  Modificación del entorno de usuario mediante la activación adecuada **herramientas** categorías o restrinja la aplicabilidad del diseñador mediante la aplicación de una instancia de la <xref:System.ComponentModel.ToolboxItemFilterAttribute>clase al diseñador.</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicialización de diseñador por un VSPackage  
 Un VSPackage debe controlar la inicialización diseñador mediante:  
  
1.  Creación de un objeto que implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>clase.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
    > [!NOTE]
    >  La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>clase nunca debe implementarse en el mismo objeto que la <xref:Microsoft.VisualStudio.Shell.Package>clase.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  Registrar la clase que implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>como proporciona compatibilidad para extensiones de VSPackage del diseñador aplicando instancias de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>y <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>a la clase proporciona la implementación de VSPackage de <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
 Cuando se crea cualquier diseñador o componente del diseñador, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno:  
  
1.  Tiene acceso a cada proveedor de extensión de la superficie de diseño registrados.  
  
2.  Crea e inicializa una instancia de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>objeto de cada proveedor extensión de la superficie de diseño</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
3.  Llama a cada proveedor de extensión de la superficie de diseño <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>método o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>(método) (según corresponda).</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 Al implementar el <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>de objeto como miembro de un paquete VSPackage, es importante comprender que:</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno no proporciona ningún control sobre qué metadatos u otras opciones de configuración de un determinado `DesignSurfaceExtension` modifica del proveedor. Es posible que dos o más `DesignSurfaceExtension` proveedores de modificar el mismo diseñador de características de las maneras en conflicto, con la modificación final que se va a definitivo. Es indeterminado, qué modificación se aplicó por última vez.  
  
2.  Es posible restringir explícitamente una implementación de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>diseñadores específicos, aplicando las instancias de objeto <xref:System.ComponentModel.ToolboxItemFilterAttribute>de dicha implementación.</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Para obtener más información sobre **herramientas** filtrado de elementos, vea <xref:System.ComponentModel.ToolboxItemFilterAttribute>y <xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>Aprovisionamiento de metadatos adicionales  
 Un VSPackage puede cambiar la configuración de un diseñador o un componente distinto del diseñador en tiempo de diseño.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>clase se puede utilizar mediante programación, o a un VSPackage que proporciona un diseñador.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>clase se utiliza para modificar los metadatos de los componentes creados en una superficie de diseño.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Por ejemplo, uno puede sustituir un Examinador de propiedades predeterminado utilizado por <xref:System.Windows.Forms.CommonDialog>objetos con un explorador de propiedades personalizado.</xref:System.Windows.Forms.CommonDialog>  
  
 Las modificaciones que proporciona una instancia de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>aplicado a la implementación de un paquete VSPackage de <xref:Microsoft.VisualStudio.Shell.Package>puede tener uno de estos dos ámbitos:</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   Global, para todas las nuevas instancias de un componente determinado  
  
-   Local--perteneciente sólo a la instancia del componente creado en una superficie de diseño proporcionada por el VSPackage actual.  
  
 El `IsGlobal` propiedad de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>instancia que se aplica a la implementación de un paquete VSPackage de <xref:Microsoft.VisualStudio.Shell.Package>determina este ámbito.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Aplicar el atributo a una implementación de <xref:Microsoft.VisualStudio.Shell.Package>con el <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>propiedad de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>objeto establecido en `true`, cambia las indicadas a continuación, el Explorador de todo el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno:</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Si se establece la marca global `false`, a continuación, el cambio de metadatos es local en el diseñador actual admitido el VSPackage actual:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  En este momento, la superficie de diseño sólo es compatible con la creación de componentes y, por lo tanto, sólo los componentes pueden tener metadatos locales. En el ejemplo anterior, nos estábamos al intentar modificar una propiedad, como el `Color` propiedad de un objeto. Si `false` se pasó a la marca global, `CustomBrowser` nunca aparecerán porque el diseñador nunca crea una instancia de `Color`. Establecer la marca global en `false` es útil para los componentes, como controles, temporizadores y cuadros de diálogo.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [Ampliar la compatibilidad en tiempo de diseño](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
