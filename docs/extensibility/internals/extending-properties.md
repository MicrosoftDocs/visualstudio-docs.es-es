---
title: Extender propiedades | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708425"
---
# <a name="extend-properties"></a>Propiedades de extensión
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ventana **propiedades** es un explorador de propiedades universal para componentes com y com+ y admite todos los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] productos. La ventana **propiedades** funciona con `ITypeInfo` información de tipos y metadatos de com+ para mostrar las propiedades en tiempo de diseño para el objeto seleccionado actualmente en cualquier otra ventana del entorno de desarrollo integrado (IDE).

 La ventana **propiedades** , que se puede abrir presionando **F4** en el teclado o seleccionando la **ventana Propiedades** en el menú **Ver** , se usa para ver y editar propiedades y eventos de tiempo de diseño independientes de la configuración y de los objetos seleccionados. Las propiedades dependientes de la configuración, asociadas a soluciones y proyectos, se muestran en [las páginas de propiedades](../../extensibility/internals/property-pages.md). Para obtener más información, [administrar las opciones de configuración](../../extensibility/internals/managing-configuration-options.md).

 ![Información general de ventana Propiedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") ventana Propiedades

 En esta sección se proporciona información detallada relacionada con las áreas individuales de la ventana **propiedades** y las interfaces que debe implementar y llamar a para rellenar la ventana.

## <a name="in-this-section"></a>En esta sección
- [Información general de ventana Propiedades](../../extensibility/internals/properties-window-overview.md)

 Explica el propósito de la ventana **propiedades** con respecto a la ventana de herramientas y la ventana de documento.

- [Directiva de plantilla y el ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Describe el modo en que un proyecto se encuentra en un proyecto de plantilla de Enterprise y cómo puede aplicar la Directiva ese proyecto de Enterprise Templates.

- [ventana Propiedades de campos e interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Explica la base para la selección que determina qué información se muestra en la ventana **propiedades** .

- [ventana Propiedades lista de objetos](../../extensibility/internals/properties-window-object-list.md)

 Describe el propósito de la lista de objetos de la ventana **propiedades** , que describe cómo, cuando un objeto diferente de esta lista desencadena una llamada, se informa al entorno de que se ha seleccionado un nuevo objeto.

- [Botones de ventana Propiedades](../../extensibility/internals/properties-window-buttons.md)

 Explica el propósito de los cuatro botones predeterminados que se muestran en la barra de herramientas de la ventana **propiedades** .

- [Cuadrícula de visualización de propiedades](../../extensibility/internals/properties-display-grid.md)

 Explica dónde se encuentran los campos nombres de propiedad y valores de propiedad en la cuadrícula.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Describe los proyectos como los bloques de creación del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Compilar y generar](../../ide/compiling-and-building-in-visual-studio.md)

 Describe cómo se puede usar la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plataforma para probar y depurar aplicaciones continuamente a medida que se crean.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Describe la `IDispatch` interfaz, que se diseñó primero para admitir la automatización, proporcionando un mecanismo enlazado en tiempo de ejecución para obtener acceso y recuperar información sobre los métodos y las propiedades de un objeto.

- [Administración de la configuración de la aplicación (.NET)](../../ide/managing-application-settings-dotnet.md)

 Proporciona información general de la configuración de la aplicación que le permite configurar la aplicación para que los valores de propiedad se almacenen en un archivo de configuración externo en lugar de en el código compilado de la aplicación.

- [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)

 Explica cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administra de forma eficaz los elementos como referencias, conexiones de datos, carpetas y archivos requeridos por el esfuerzo de desarrollo a través de soluciones y proyectos.

- [Extender otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Explica cómo usar los servicios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para crear elementos de interfaz de usuario que coincidan con el resto de servicios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
