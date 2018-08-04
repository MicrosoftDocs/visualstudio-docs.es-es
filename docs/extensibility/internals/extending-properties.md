---
title: Extender propiedades | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77b5861dd084098e561f3642b5738dd0279d4b52
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512114"
---
# <a name="extend-properties"></a>Extender propiedades
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propiedades** ventana es un explorador de propiedades universal para los componentes COM y COM + y admite todas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] productos. El **propiedades** ventana funciona con `ITypeInfo` escriba la información y los metadatos de COM + para enumerar las propiedades de tiempo de diseño para el objeto seleccionado actualmente en otra ventana en el entorno de desarrollo integrado (IDE).  
  
 El **propiedades** ventana, que se puede abrir presionando **F4** en el teclado, o seleccionar **ventana propiedades** en el **vista** menú, se usa para ver y editar propiedades de tiempo de diseño independientes de la configuración y los eventos de los objetos seleccionados. Propiedades dependientes de la configuración, asociadas con soluciones y proyectos, se muestran en [páginas de propiedades](../../extensibility/internals/property-pages.md). Para obtener más información, [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Información general sobre la ventana de propiedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Propiedades (ventana)  
  
 Esta sección proporciona información detallada relacionada con las áreas individuales de la **propiedades** ventana y las interfaces que debe implementar y llamada a rellenar la ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general sobre la ventana de propiedades](../../extensibility/internals/properties-window-overview.md)  
 Explica el propósito de la **propiedades** ventana con respecto a la ventana de herramientas y la ventana de documento.  
  
 [Directiva de plantilla y la ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Describe cómo un proyecto se encuentra en una plantilla de proyecto y cómo esa plantilla de proyecto puede aplicar directivas.  
  
 [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica la base para la selección que determina qué información se muestra en el **propiedades** ventana.  
  
 [Lista de objetos de ventana de propiedades](../../extensibility/internals/properties-window-object-list.md)  
 Describe el propósito de la **propiedades** lista de objetos de ventana, que describe cómo hacerlo, cuando un objeto diferente de esta lista desencadena una llamada, el entorno se informa que se ha seleccionado un nuevo objeto.  
  
 [Botones de la ventana Propiedades](../../extensibility/internals/properties-window-buttons.md)  
 Explica el propósito de los botones de cuatro predeterminados mostrados en la **propiedades** barra de herramientas de ventana.  
  
 [Mostrar cuadrícula de propiedades](../../extensibility/internals/properties-display-grid.md)  
 Explica dónde se encuentran los nombres de propiedad y los campos de valores de propiedad en la cuadrícula.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe los proyectos como los bloques de creación de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compilar y generar](../../ide/compiling-and-building-in-visual-studio.md)  
 Describe cómo puede usar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plataforma para probar y depurar aplicaciones como proceso de compilación continuamente.  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 Describe el `IDispatch` interfaz, que primero se diseñó para admitir la automatización, que proporciona un mecanismo de tiempo de ejecución para acceder y recuperar información acerca de los métodos y propiedades de un objeto.  
  
 [Administración de la configuración de la aplicación (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Proporciona información general de configuración de la aplicación que le permiten configurar la aplicación para que los valores de propiedad se almacenan en un archivo de configuración externo en lugar de código compilado de la aplicación.  
  
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administra con eficacia los elementos como las referencias, las conexiones de datos, carpetas y archivos necesarios para el desarrollo a través de soluciones y proyectos.  
  
 [Extender otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servicios para crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].