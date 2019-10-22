---
title: Extender propiedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee70a4d88dfc6eb1dae5c0d8fba0fb1deb7a7621
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332190"
---
# <a name="extend-properties"></a>Extender propiedades
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propiedades** ventana es un explorador de propiedades universal para los componentes COM y COM + y admite todas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] productos. El **propiedades** ventana funciona con `ITypeInfo` escriba la información y los metadatos de COM + para enumerar las propiedades de tiempo de diseño para el objeto seleccionado actualmente en otra ventana en el entorno de desarrollo integrado (IDE).

 El **propiedades** ventana, que se puede abrir presionando **F4** en el teclado, o seleccionar **ventana propiedades** en el **vista** menú, se usa para ver y editar propiedades de tiempo de diseño independientes de la configuración y los eventos de los objetos seleccionados. Propiedades dependientes de la configuración, asociadas con soluciones y proyectos, se muestran en [páginas de propiedades](../../extensibility/internals/property-pages.md). Para obtener más información, [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).

 ![Información general sobre la ventana de propiedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") ventana Propiedades

 Esta sección proporciona información detallada relacionada con las áreas individuales de la **propiedades** ventana y las interfaces que debe implementar y llamada a rellenar la ventana.

## <a name="in-this-section"></a>En esta sección
- [Información general sobre la ventana de propiedades](../../extensibility/internals/properties-window-overview.md)

 Explica el propósito de la **propiedades** ventana con respecto a la ventana de herramientas y la ventana de documento.

- [Directiva de plantilla y la ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Describe cómo un proyecto se encuentra en una plantilla de proyecto y cómo esa plantilla de proyecto puede aplicar directivas.

- [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Explica la base para la selección que determina qué información se muestra en el **propiedades** ventana.

- [Lista de objetos de ventana de propiedades](../../extensibility/internals/properties-window-object-list.md)

 Describe el propósito de la **propiedades** lista de objetos de ventana, que describe cómo hacerlo, cuando un objeto diferente de esta lista desencadena una llamada, el entorno se informa que se ha seleccionado un nuevo objeto.

- [Botones de la ventana Propiedades](../../extensibility/internals/properties-window-buttons.md)

 Explica el propósito de los botones de cuatro predeterminados mostrados en la **propiedades** barra de herramientas de ventana.

- [Mostrar cuadrícula de propiedades](../../extensibility/internals/properties-display-grid.md)

 Explica dónde se encuentran los nombres de propiedad y los campos de valores de propiedad en la cuadrícula.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Describe los proyectos como los bloques de creación de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Compilar y generar](../../ide/compiling-and-building-in-visual-studio.md)

 Describe cómo puede usar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plataforma para probar y depurar aplicaciones como proceso de compilación continuamente.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Describe el `IDispatch` interfaz, que primero se diseñó para admitir la automatización, que proporciona un mecanismo de tiempo de ejecución para acceder y recuperar información acerca de los métodos y propiedades de un objeto.

- [Administración de la configuración de la aplicación (.NET)](../../ide/managing-application-settings-dotnet.md)

 Proporciona información general de configuración de la aplicación que le permiten configurar la aplicación para que los valores de propiedad se almacenan en un archivo de configuración externo en lugar de código compilado de la aplicación.

- [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)

 Explica cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administra con eficacia los elementos como las referencias, las conexiones de datos, carpetas y archivos necesarios para el desarrollo a través de soluciones y proyectos.

- [Extender otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Explica cómo usar los servicios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para crear elementos de interfaz de usuario que coincidan con el resto de servicios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].