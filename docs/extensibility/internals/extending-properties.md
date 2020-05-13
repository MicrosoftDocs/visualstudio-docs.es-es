---
title: Ampliación de las propiedades de la sección de propiedades de Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708425"
---
# <a name="extend-properties"></a>Extender propiedades
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ventana **Propiedades** es un explorador de propiedades universal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para componentes COM y COM+ y admite todos los productos. La **Properties** ventana Propiedades `ITypeInfo` funciona con información de tipo y metadatos COM+ para enumerar las propiedades en tiempo de diseño del objeto seleccionado actualmente en cualquier otra ventana del entorno de desarrollo integrado (IDE).

 La ventana **Propiedades,** que se puede abrir presionando **F4** en el teclado o seleccionando **Ventana Propiedades** en el menú **Ver,** se utiliza para ver y editar propiedades y eventos en tiempo de diseño independientes de la configuración de los objetos seleccionados. Las propiedades dependientes de la configuración, asociadas a soluciones y proyectos, se muestran en [las páginas de propiedades.](../../extensibility/internals/property-pages.md) Para obtener más información, [administrar opciones](../../extensibility/internals/managing-configuration-options.md)de configuración .

 ![Descripción general de la ventana Propiedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Ventana Propiedades

 Esta sección proporciona información detallada que se relaciona con las áreas individuales de la ventana **Propiedades** y las interfaces que debe implementar y llamar para rellenar la ventana.

## <a name="in-this-section"></a>En esta sección
- [Descripción general de la ventana Propiedades](../../extensibility/internals/properties-window-overview.md)

 Explica el propósito de la ventana **Propiedades** en relación con la ventana de herramientas y la ventana del documento.

- [Directiva de plantilla y la ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Describe cómo un proyecto está contenido en un proyecto de plantilla de empresa y cómo ese proyecto de plantilla de empresa puede aplicar la directiva.

- [Propiedades campos de ventana e interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Explica la base de la selección que determina qué información se muestra en la ventana **Propiedades.**

- [Lista de objetos de la ventana Propiedades](../../extensibility/internals/properties-window-object-list.md)

 Describe el propósito de la lista de objetos de ventana **Propiedades,** que describe cómo, cuando un objeto diferente de esta lista desencadena una llamada, se informa al entorno de que se ha seleccionado un nuevo objeto.

- [Botones de la ventana Propiedades](../../extensibility/internals/properties-window-buttons.md)

 Explica el propósito de los cuatro botones predeterminados que se muestran en la barra de herramientas de la ventana **Propiedades.**

- [Cuadrícula de visualización de propiedades](../../extensibility/internals/properties-display-grid.md)

 Explica dónde se encuentran los nombres de propiedad y los campos de valores de propiedad en la cuadrícula.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Describe los proyectos como los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bloques de creación del IDE.

- [Compilar y generar](../../ide/compiling-and-building-in-visual-studio.md)

 Describe cómo puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la plataforma para probar y depurar aplicaciones continuamente a medida que las compila.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Describe la `IDispatch` interfaz, que se diseñó primero para admitir la automatización, proporcionando un mecanismo enlazado en tiempo de que se va a tiempo para tener acceso y recuperar información sobre los métodos y propiedades de un objeto.

- [Administración de la configuración de la aplicación (.NET)](../../ide/managing-application-settings-dotnet.md)

 Proporciona información general sobre la configuración de la aplicación que le permite configurar la aplicación para que los valores de propiedad se almacenen en un archivo de configuración externo en lugar del código compilado de la aplicación.

- [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)

 Explica [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cómo se administran de forma eficaz los elementos, como referencias, conexiones de datos, carpetas y archivos que requiere el esfuerzo de desarrollo a través de soluciones y proyectos.

- [Ampliar otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Explica cómo usar los servicios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para crear elementos de interfaz de usuario que coincidan con el resto de servicios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
