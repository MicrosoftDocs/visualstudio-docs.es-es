---
title: Inicialización del diseñador y configuración de metadatos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712223"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicialización del diseñador y configuración de metadatos

La manipulación de los metadatos y atributos de filtro asociados a un diseñador o componente <xref:System.Type> de diseñador proporciona un mecanismo para que las aplicaciones definan qué herramientas usa un diseñador determinado para controlar diferentes objetos (como estructuras de datos, clases o entidades gráficas), cuando el diseñador está disponible y cómo el IDE de Visual Studio está configurado para admitir el diseñador (por ejemplo, qué categoría o pestaña de **Toolbox** está disponible).

Proporciona [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] varios mecanismos para facilitar el control de la inicialización de un diseñador o componente de diseñador y la manipulación de sus metadatos por un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inicializar metadatos e información de configuración
 Dado que se cargan a petición, VSPackages puede no haber sido cargado por el entorno de Visual Studio antes de la creación de instancias de un diseñador. Por lo tanto, VSPackages no puede usar el mecanismo estándar para configurar <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> un diseñador o componente de diseñador en la creación, que es controlar un evento. En su lugar, un VSPackage <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementa una instancia de la interfaz y se registra para proporcionar personalizaciones, denominadas extensiones de superficie de diseño.

### <a name="customize-initialization"></a>Personalizar la inicialización

Personalizar un diseñador, un componente o una superficie de diseñador implica:

1. Modificar los metadatos del diseñador <xref:System.Type> y cambiar eficazmente el acceso o la conversión de un determinado.

    Esto se hace típicamente <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> a través de los mecanismos o.

    Por ejemplo, <xref:System.Windows.Forms>cuando se inicializan diseñadores basados <xref:System.Drawing.Design.UITypeEditor> en <xref:System.Web.UI.WebControls.Image> -, el entorno de Visual Studio modifica los objetos for utilizados con el diseñador para usar el administrador de recursos para obtener mapas de bits en lugar del sistema de archivos.

2. Integración con el entorno, por ejemplo, suscribiéndose a eventos u obteniendo información de configuración del proyecto. Puede obtener información de configuración del proyecto <xref:System.ComponentModel.Design.ITypeResolutionService> y suscribirse a eventos obteniendo la interfaz.

3. Modificación del entorno de usuario activando las categorías de **Toolbox** adecuadas o restringiendo la aplicabilidad del diseñador aplicando una instancia de la <xref:System.ComponentModel.ToolboxItemFilterAttribute> clase al diseñador.

### <a name="designer-initialization-by-a-vspackage"></a>Inicialización del diseñador por un VSPackage

Un VSPackage debe controlar la inicialización del diseñador mediante:

1. Crear un objeto <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> que implementa la clase.

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> clase nunca debe implementarse en <xref:Microsoft.VisualStudio.Shell.Package> el mismo objeto que la clase.

2. Registrar la clase que <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementa como proporcionar compatibilidad con las extensiones de diseñador de VSPackage. Registre la clase aplicando <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>instancias de , <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>, y <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> a la <xref:Microsoft.VisualStudio.Shell.Package>clase que proporciona la implementación de VSPackage de .

Cada vez que se crea un diseñador o componente de diseñador, el entorno de Visual Studio:

- Tiene acceso a cada proveedor de extensión de superficie de diseño registrado.

- Crea una instancia e inicializa una instancia del <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto de cada proveedor de extensión de superficie de diseño.

- Llama al método o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> método <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> de cada proveedor de extensión de superficie de diseño (según corresponda).

Al implementar <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> el objeto como miembro de un VSPackage, es importante entender que:

- El entorno de Visual Studio no proporciona ningún control `DesignSurfaceExtension` sobre qué metadatos u otras opciones de configuración modifica un proveedor determinado. Es posible que dos `DesignSurfaceExtension` o más proveedores modifiquen la misma característica de diseñador de maneras conflictivas, siendo la modificación final definitiva. Es indeterminado qué modificación se aplica por última vez.

- Es posible restringir explícitamente una implementación del <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto a diseñadores <xref:System.ComponentModel.ToolboxItemFilterAttribute> específicos aplicando instancias de esa implementación. Para obtener más información sobre <xref:System.ComponentModel.ToolboxItemFilterAttribute> el <xref:System.ComponentModel.ToolboxItemFilterType>filtrado de elementos de **Toolbox,** vea el archivo y .

## <a name="additional-metadata-provisioning"></a>Aprovisionamiento de metadatos adicionales

Un VSPackage puede cambiar la configuración de un diseñador o componente de diseñador que no sea en tiempo de diseño.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> clase se puede usar mediante programación o aplicar a un VSPackage que proporciona un diseñador.

Una instancia <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> de la clase se utiliza para modificar los metadatos de los componentes creados en una superficie de diseño. Por ejemplo, se podría reemplazar un <xref:System.Windows.Forms.CommonDialog> explorador de propiedades predeterminado utilizado por los objetos con un explorador de propiedades personalizado.

Las modificaciones proporcionadas <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> por una instancia de <xref:Microsoft.VisualStudio.Shell.Package> aplicado a la implementación de un VSPackage de pueden tener uno de dos ámbitos:

- Global -- para todas las nuevas instancias de un componente determinado

- Local: pertenece solo a la instancia del componente creado en una superficie de diseño proporcionada por el VSPackage actual.

La `IsGlobal` propiedad <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> de la instancia aplicada a <xref:Microsoft.VisualStudio.Shell.Package> la implementación de un VSPackage de determina este ámbito.

Aplicar el atributo a <xref:Microsoft.VisualStudio.Shell.Package> una <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> implementación <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> de con `true`la propiedad del objeto establecido en , como se muestra a continuación, cambia el explorador para todo el entorno de Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Si la marca global `false`se estableció en , el cambio de metadatos es local para el diseñador actual admitido por el VSPackage actual:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> La superficie de diseño solo admite la creación de componentes y, por lo tanto, solo los componentes pueden tener metadatos locales. En el ejemplo anterior, intentamos modificar una propiedad, como la `Color` propiedad de un objeto. Si `false` se pasó para la `CustomBrowser` marca global, nunca aparecería `Color`porque el diseñador nunca crea realmente una instancia de . Establecer la marca `false` global en es útil para los componentes, como controles, temporizadores y cuadros de diálogo.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Amplíe el soporte en tiempo de diseño](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
