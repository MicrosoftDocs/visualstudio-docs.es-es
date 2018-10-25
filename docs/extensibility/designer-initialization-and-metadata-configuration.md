---
title: Inicialización de diseñador y configuración de los metadatos | Microsoft Docs
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
ms.openlocfilehash: 58f103ae1dcf445c5bdfe322eeea7a88a7b25683
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843280"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Configuración de inicialización y metadatos del diseñador
Manipulación de los atributos de metadatos y el filtro asociado con un diseñador o un componente del diseñador proporciona un mecanismo para las aplicaciones definir qué herramientas se usan un diseñador concreto para controlar diferentes <xref:System.Type> objetos (por ejemplo, las estructuras de datos las clases o entidades gráficas), cuando el diseñador está disponible, y cómo se configura el IDE de Visual Studio para admitir el diseñador (para la instancia que **cuadro de herramientas** categoría o pestaña está disponible).  
  
 El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona varios mecanismos para facilitar el control de la inicialización del diseñador o el componente de diseñador y la manipulación de sus metadatos de un VSPackage.  
  
## <a name="initialize-metadata-and-configuration-information"></a>Inicializar la información de configuración y metadatos  
 Porque se cargan a petición, los paquetes VSPackage es posible que no se hayan cargado por el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno antes de la creación de instancias de un diseñador. Por lo tanto, los VSPackages no puede usar el mecanismo estándar para configurar un diseñador o un componente del diseñador en la creación, que se va a controlar un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> eventos. En su lugar, un VSPackage implementa una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfaz y registra automáticamente para proporcionar las personalizaciones, que se conocen como extensiones de superficie de diseño.  
  
### <a name="customize-initialization"></a>Personalizar la inicialización  
 Personalización de un diseñador, un componente o una superficie del diseñador, implica:  
  
1. Modificar los metadatos del diseñador y cambiar de forma efectiva cómo una determinada <xref:System.Type> se tiene acceso a o se convierten.  
  
    Esto se hace normalmente a través de la <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.TypeConverter> mecanismos.  
  
    Por ejemplo, cuando <xref:System.Windows.Forms>-se inicializan en función de los diseñadores, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno modifica el <xref:System.Drawing.Design.UITypeEditor> para <xref:System.Web.UI.WebControls.Image> los objetos utilizados con el diseñador para utilizar el Administrador de recursos para obtener los mapas de bits en lugar de con el sistema de archivos.  
  
2. La integración con el entorno, por ejemplo, al suscribirse a eventos o la obtención de información de configuración del proyecto. Puede obtener información de configuración de proyecto y suscribirse a eventos mediante la obtención de la <xref:System.ComponentModel.Design.ITypeResolutionService> interfaz.  
  
3. Modificación del entorno del usuario mediante la activación adecuada **cuadro de herramientas** categorías o restringiendo la aplicabilidad del diseñador mediante la aplicación de una instancia de la <xref:System.ComponentModel.ToolboxItemFilterAttribute> clase al diseñador.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicialización de diseñador un VSPackage  
 Un VSPackage debe controlar la inicialización de diseñador por:  
  
1. Creación de un objeto que implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> clase.  
  
   > [!NOTE]
   >  El <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> clase nunca debe implementarse en el mismo objeto que la <xref:Microsoft.VisualStudio.Shell.Package> clase.  
  
2. Registrar la clase que implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> como proporcionar soporte técnico para las extensiones de VSPackage del diseñador aplicando las instancias de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> a la clase que proporciona una implementación de VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   Cada vez que se crea cualquier diseñador o el componente del diseñador, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno:  
  
3. Tiene acceso a cada proveedor de extensión de la superficie de diseño registrados.  
  
4. Crea una instancia e inicializa una instancia de cada proveedor de extensión de la superficie de diseño <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto  
  
5. Llama a cada proveedor de extensión de la superficie de diseño <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> método o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> método (según corresponda).  
  
   Al implementar el <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto como un miembro de un VSPackage, es importante comprender que:  
  
6. El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno no proporciona ningún control sobre qué metadatos u otras opciones de configuración de un determinado `DesignSurfaceExtension` modifica del proveedor. Es posible que dos o más `DesignSurfaceExtension` proveedores de modificar el mismo diseñador de características de las maneras en conflicto, con la modificación final que se va a definitivo. Es indeterminado qué modificación se aplica por última vez.  
  
7. Es posible restringir explícitamente una implementación de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> diseñadores específicos, aplicando las instancias de objeto <xref:System.ComponentModel.ToolboxItemFilterAttribute> para esa implementación. Para obtener más información sobre **cuadro de herramientas** filtrado de elementos, vea el <xref:System.ComponentModel.ToolboxItemFilterAttribute> y <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Aprovisionamiento de metadatos adicionales  
 Un VSPackage puede cambiar la configuración de un diseñador o un componente distinto del diseñador en tiempo de diseño.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> clase puede usarse mediante programación, o se puede aplicar a un VSPackage que proporciona un diseñador.  
  
 Una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> clase se utiliza para modificar los metadatos de los componentes creados en una superficie de diseño. Por ejemplo, uno podría reemplazar un Examinador de propiedades predeterminado utilizado por <xref:System.Windows.Forms.CommonDialog> objetos con un explorador de propiedades personalizado.  
  
 Las modificaciones que se proporciona una instancia de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> aplicado a la implementación de un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> puede tener uno de estos dos ámbitos:  
  
- Global: para todas las nuevas instancias de un componente determinado  
  
- Local--perteneciente sólo a la instancia del componente creado en una superficie de diseño proporcionada por el VSPackage actual.  
  
  El `IsGlobal` propiedad de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instancia que se aplica a la implementación de un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> determina este ámbito.  
  
  Aplicar el atributo a una implementación de <xref:Microsoft.VisualStudio.Shell.Package> con el <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> propiedad de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> objeto establecido en `true`, cambia las indicadas a continuación, el explorador para toda la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Si la marca global se estableció en `false`, a continuación, el cambio de metadatos es local en el diseñador actual compatible con el paquete VSPackage actual:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  En este momento, la superficie de diseño solo admite la creación de componentes y, por lo tanto, solo los componentes pueden tener metadatos locales. En el ejemplo anterior, nos estábamos intentando modificar una propiedad, como el `Color` propiedad de un objeto. Si `false` se pasó a la marca global, `CustomBrowser` no aparecería nunca porque el diseñador crea nunca realmente una instancia de `Color`. Establecer la marca global en `false` es útil para los componentes, como controles, temporizadores y los cuadros de diálogo.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Ampliar la compatibilidad en tiempo de diseño](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)