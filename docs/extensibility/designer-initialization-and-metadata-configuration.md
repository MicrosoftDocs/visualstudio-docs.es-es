---
title: Inicialización del diseñador y configuración de metadatos | Microsoft Docs
description: Obtenga información sobre cómo el SDK de Visual Studio facilita el control de la inicialización y los metadatos de los componentes de un diseñador o del diseñador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 57e335839905e828d3587ce82b1e23b0d62ddf65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968325"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicialización del diseñador y configuración de metadatos

La manipulación de los metadatos y los atributos de filtro asociados a un diseñador o componente de diseñador proporciona un mecanismo para que las aplicaciones definan qué herramientas usa un diseñador determinado para controlar <xref:System.Type> objetos diferentes (como estructuras de datos, clases o entidades gráficas), Cuándo está disponible el diseñador y cómo está configurado el IDE de Visual Studio para admitir el diseñador (por ejemplo, la categoría o pestaña del **cuadro**

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Proporciona varios mecanismos para facilitar el control de la inicialización de un diseñador o del componente de diseñador y la manipulación de sus metadatos por parte de un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inicializar metadatos e información de configuración
 Dado que se cargan a petición, es posible que el entorno de Visual Studio no haya cargado VSPackages antes de la creación de instancias de un diseñador. Por lo tanto, los VSPackages no pueden utilizar el mecanismo estándar para configurar un diseñador o componente de diseñador al crear, que es para controlar un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> evento. En su lugar, un VSPackage implementa una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfaz y se registra para proporcionar personalizaciones, denominadas extensiones de superficie de diseño.

### <a name="customize-initialization"></a>Personalizar inicialización

La personalización de un diseñador, un componente o una superficie del diseñador implica:

1. Modificar los metadatos del diseñador y cambiar de forma eficaz cómo <xref:System.Type> se obtiene acceso a determinados o se convierten.

    Normalmente, esto se realiza a través de los <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> mecanismos o.

    Por ejemplo, cuando <xref:System.Windows.Forms> se inicializan los diseñadores basados en, el entorno de Visual Studio modifica <xref:System.Drawing.Design.UITypeEditor> el <xref:System.Web.UI.WebControls.Image> objeto para los objetos que se usan con el diseñador para usar el administrador de recursos con el fin de obtener mapas de bits en lugar del sistema de archivos.

2. Integración con el entorno, por ejemplo, mediante la suscripción a eventos u obtención de información de configuración del proyecto. Puede obtener la información de configuración del proyecto y suscribirse a eventos obteniendo la <xref:System.ComponentModel.Design.ITypeResolutionService> interfaz.

3. Modificación del entorno del usuario mediante la activación de las categorías apropiadas del **cuadro de herramientas** o mediante la restricción de la aplicabilidad del diseñador mediante la aplicación de una instancia de la <xref:System.ComponentModel.ToolboxItemFilterAttribute> clase al diseñador.

### <a name="designer-initialization-by-a-vspackage"></a>Inicialización del diseñador mediante un VSPackage

Un VSPackage debe controlar la inicialización del diseñador mediante:

1. Crear un objeto que implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> clase.

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> clase nunca debe implementarse en el mismo objeto que la <xref:Microsoft.VisualStudio.Shell.Package> clase.

2. Registrar la clase que implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> para proporcionar compatibilidad con las extensiones de diseñador del VSPackage. Registre la clase aplicando instancias de  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> , <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> a la clase que proporciona la implementación del VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> .

Cada vez que se crea un diseñador o componente de diseñador, el entorno de Visual Studio:

- Obtiene acceso a cada proveedor de extensión de la superficie de diseño registrada.

- Crea instancias e inicializa una instancia de cada objeto del proveedor de extensión de la superficie de diseño <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> .

- Llama a cada método o método del proveedor de la extensión de la superficie de diseño <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (según corresponda).

Al implementar el <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto como miembro de un VSPackage, es importante comprender esto:

- El entorno de Visual Studio no proporciona ningún control sobre qué metadatos u otros valores de configuración `DesignSurfaceExtension` modifica un proveedor determinado. Es posible que dos o más `DesignSurfaceExtension` proveedores modifiquen la misma característica del diseñador de maneras conflictivas, con lo que la modificación final es definitiva. Es indeterminado qué modificación se aplica por última vez.

- Es posible restringir explícitamente una implementación del <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objeto a diseñadores específicos aplicando instancias de <xref:System.ComponentModel.ToolboxItemFilterAttribute> a esa implementación. Para obtener más información sobre el filtrado de elementos del **cuadro de herramientas** , vea <xref:System.ComponentModel.ToolboxItemFilterAttribute> y <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>Aprovisionamiento de metadatos adicional

Un VSPackage puede cambiar la configuración de un diseñador o un componente del diseñador que no sea en tiempo de diseño.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> clase se puede usar mediante programación o se puede aplicar a un VSPackage que proporciona un diseñador.

Se utiliza una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> clase para modificar los metadatos de los componentes creados en una superficie de diseño. Por ejemplo, puede reemplazar un explorador de propiedades predeterminado utilizado por los <xref:System.Windows.Forms.CommonDialog> objetos con un explorador de propiedades personalizado.

Las modificaciones proporcionadas por una instancia de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> que se aplica a la implementación de un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> pueden tener uno de dos ámbitos:

- Global: para todas las instancias nuevas de un componente determinado

- Local: pertenece únicamente a la instancia del componente creado en una superficie de diseño proporcionada por el VSPackage actual.

La `IsGlobal` propiedad de la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instancia de que se aplica a la implementación de un VSPackage de <xref:Microsoft.VisualStudio.Shell.Package> determina este ámbito.

Al aplicar el atributo a una implementación de <xref:Microsoft.VisualStudio.Shell.Package> con la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> propiedad del <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> objeto establecido en `true` , como se indica a continuación, se cambia el explorador para todo el entorno de Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Si la marca global se estableció en `false` , el cambio de metadatos es local en el diseñador actual admitido por el VSPackage actual:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> La superficie de diseño solo admite la creación de componentes y, por lo tanto, solo los componentes pueden tener metadatos locales. En el ejemplo anterior, estábamos intentando modificar una propiedad, como la `Color` propiedad de un objeto. Si `false` se pasó para la marca global, `CustomBrowser` nunca aparecería porque el diseñador nunca crea realmente una instancia de `Color` . Establecer la marca global en `false` es útil para los componentes, como los controles, los temporizadores y los cuadros de diálogo.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Ampliar la compatibilidad en tiempo de diseño](/previous-versions/37899azc(v=vs.140))