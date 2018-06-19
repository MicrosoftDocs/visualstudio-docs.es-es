---
title: Inicialización de diseñador y la configuración de metadatos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6334f65b942b2eab3543d866ae1b98a186569ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132752"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicialización de diseñador y la configuración de metadatos
Manipulación de los atributos de metadatos y el filtro asociado a un diseñador o un componente del diseñador proporciona un mecanismo para que las aplicaciones definir las herramientas que se usan un determinado diseñador para controlar diferentes <xref:System.Type> objetos (por ejemplo, las estructuras de datos clases, o entidades gráficas), cuando el diseñador está disponible, y cómo el IDE de Visual Studio está configurado para admitir el diseñador (para la instancia que **cuadro de herramientas** categoría o pestaña está disponible).  
  
 El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona varios mecanismos para facilitar el control de la inicialización del diseñador o del componente del diseñador y la manipulación de los metadatos por un paquete VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicializando metadatos e información de configuración  
 Porque se cargan a petición, VSPackages que no se han cargado por el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno antes de la creación de instancias de un diseñador. Por lo tanto, VSPackages no puede usar el mecanismo estándar para configurar un diseñador o un componente del diseñador cuando se crea, que se usa para controlar un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> eventos. En su lugar, un VSPackage implementa una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfaz y registra automáticamente para proporcionar las personalizaciones, denominadas extensiones de superficie de diseño.  
  
### <a name="customizing-initialization"></a>Personalizar la inicialización  
 Personalización de un diseñador, un componente o una superficie del diseñador, implica:  
  
1.  Modificar los metadatos del diseñador y cambiar de forma efectiva cómo un determinado <xref:System.Type> se tiene acceso o se convierten.  
  
     Esto se hace normalmente a través de la <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.TypeConverter> mecanismos.  
  
     Por ejemplo, cuando <xref:System.Windows.Forms>-se inicializan en función de los diseñadores, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno modifica la <xref:System.Drawing.Design.UITypeEditor> para <xref:System.Web.UI.WebControls.Image> objetos usados con el diseñador para utilizar el Administrador de recursos para obtener los mapas de bits en lugar de con el sistema de archivos.  
  
2.  Integración con el entorno, por ejemplo, al suscribirse a eventos o la obtención de información de configuración de proyecto. Puede obtener información de configuración de proyecto y suscribirse a eventos mediante la obtención de la <xref:System.ComponentModel.Design.ITypeResolutionService> interfaz.  
  
3.  Modificación del entorno de usuario mediante la activación adecuada **cuadro de herramientas** categorías o mediante la restricción de aplicabilidad del diseñador mediante la aplicación de una instancia de la <xref:System.ComponentModel.ToolboxItemFilterAttribute> clase al diseñador.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicialización de diseñador por un paquete VSPackage  
 Un VSPackage debe controlar la inicialización de diseñador por:  
  
1.  Crear un objeto que implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> clase.  
  
    > [!NOTE]
    >  El <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> clase nunca debe implementarse en el mismo objeto que la <xref:Microsoft.VisualStudio.Shell.Package> clase.  
  
2.  Registrar la clase que implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> como proporcionar soporte técnico para las extensiones del Diseñador de VSPackage mediante la aplicación de instancias de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> a la clase que proporciona la implementación de VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 Cada vez que se crea ningún diseñador o un componente del diseñador, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno:  
  
1.  Tiene acceso a cada proveedor de extensión de la superficie de diseño registrados.  
  
2.  Crea e inicializa una instancia de cada proveedor de extensión de la superficie de diseño <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto  
  
3.  Llama a cada proveedor de extensión de la superficie de diseño <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> método o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> método (según corresponda).  
  
 Al implementar la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> del objeto como un miembro de un VSPackage, es importante saber que:  
  
1.  El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno no proporciona ningún control sobre qué metadatos u otras opciones de configuración de un determinado `DesignSurfaceExtension` modifica del proveedor. Es posible que dos o más `DesignSurfaceExtension` proveedores de modificación de la misma característica Diseñador de maneras en conflicto, con la modificación final que se va a definitiva. Es indeterminado qué modificación se aplicó por última vez.  
  
2.  Es posible restringir explícitamente una implementación de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto diseñadores específicos, mediante la aplicación de instancias de <xref:System.ComponentModel.ToolboxItemFilterAttribute> para que la implementación. Para obtener más información sobre **cuadro de herramientas** filtrado de elementos, vea el <xref:System.ComponentModel.ToolboxItemFilterAttribute> y <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Aprovisionamiento de metadatos adicionales  
 Un VSPackage puede cambiar la configuración de un diseñador o un componente del diseñador distinto en tiempo de diseño.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> clase se puede utilizar mediante programación, o se aplica a un paquete VSPackage proporciona un diseñador.  
  
 Una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> clase se utiliza para modificar los metadatos de los componentes creados en una superficie de diseño. Por ejemplo, uno puede sustituir un Examinador de propiedades predeterminado utilizado por <xref:System.Windows.Forms.CommonDialog> objetos con un explorador de propiedades personalizadas.  
  
 Las modificaciones que se proporciona una instancia de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> aplicado a la implementación de un paquete VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> puede tener uno de los dos ámbitos:  
  
-   Global: para todas las nuevas instancias de un componente determinado  
  
-   Local--pertenecen únicamente a la instancia del componente creado en una superficie de diseño proporcionada por el VSPackage actual.  
  
 El `IsGlobal` propiedad de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instancia que se aplica a la implementación de un paquete VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> determina este ámbito.  
  
 Aplicar el atributo a una implementación de <xref:Microsoft.VisualStudio.Shell.Package> con el <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> propiedad de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> objeto establecido en `true`, cambia a la siguiente, el explorador para toda la colección [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Si la marca global se estableció en `false`, a continuación, el cambio de metadatos es local para el diseñador actual admitido por el VSPackage actual:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  En este momento, la superficie de diseño solo es compatible con la creación de componentes y, por lo tanto, sólo los componentes pueden tener metadatos locales. En el ejemplo anterior, se nos ha intentando modificar una propiedad, como el `Color` propiedad de un objeto. Si `false` se pasó a la marca global, `CustomBrowser` no aparecería nunca porque el diseñador nunca crea una instancia de `Color`. Establecer la marca global en `false` es útil para los componentes, como controles, temporizadores y cuadros de diálogo.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Ampliar compatibilidad en tiempo de diseño](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)