---
title: Extender propiedades | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 26cf161259736dbd2b2e26279842571d62f69352
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="extending-properties"></a>Extender propiedades
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propiedades** ventana es un explorador de propiedades universal para los componentes COM y COM + y admite todas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] productos. El **propiedades** ventana funciona con `ITypeInfo` escriba la información y metadatos de COM + para mostrar las propiedades de tiempo de diseño para el objeto seleccionado actualmente en cualquier otra ventana en el entorno de desarrollo integrado (IDE).  
  
 El **propiedades** ventana, que se puede abrir si se presiona F4 en el teclado o seleccionando **ventana propiedades** en el **vista** menú, se utiliza para ver y editar propiedades de tiempo de diseño independientes de la configuración y los eventos de los objetos seleccionados. Propiedades dependientes de la configuración, asociadas con soluciones y proyectos, se muestran en [páginas de propiedades](../../extensibility/internals/property-pages.md). Para obtener más información, [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Información general sobre la ventana de propiedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Propiedades (ventana)  
  
 Esta sección proporciona información detallada que se relaciona con las áreas individuales de la **propiedades** ventana y las interfaces que debe implementar y llamada para rellenar la ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general sobre la ventana Propiedades](../../extensibility/internals/properties-window-overview.md)  
 Explica el propósito de la **propiedades** ventana con respecto a la ventana de herramientas y la ventana de documento.  
  
 [Directiva de plantilla y ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Describe cómo un proyecto se encuentra en un proyecto de enterprise Templates y cómo ese proyecto de enterprise Templates puede aplicar directivas.  
  
 [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica la base para la selección que determina qué información se muestra en el **propiedades** ventana.  
  
 [Lista de objetos de la ventana Propiedades](../../extensibility/internals/properties-window-object-list.md)  
 Describe el propósito de la **propiedades** lista de objetos de ventana, que describe cómo, cuando un objeto diferente de esta lista desencadena una llamada, el entorno se informa que se ha seleccionado un nuevo objeto.  
  
 [Botones de la ventana Propiedades](../../extensibility/internals/properties-window-buttons.md)  
 Explica el propósito de los botones de cuatro predeterminados que se muestran en la **propiedades** barra de herramientas de ventana.  
  
 [Cuadrícula para mostrar de Propiedades](../../extensibility/internals/properties-display-grid.md)  
 Explica dónde se encuentran los nombres de propiedad y los campos de valores de propiedad en la cuadrícula.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe los proyectos como bloques de creación de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)  
 Describe cómo puede utilizar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plataforma para probar y depurar aplicaciones como proceso de compilación continuamente.  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 Describe el `IDispatch` interfaz, que se diseñó inicialmente para admitir la automatización, proporcionar un mecanismo de tiempo de ejecución para obtener acceso y recuperar información sobre los métodos y propiedades de un objeto.  
  
 [Administrar configuración de la aplicación (. NET)](../../ide/managing-application-settings-dotnet.md)  
 Proporciona información general de configuración de la aplicación que le permiten configurar la aplicación para que los valores de propiedad se almacenan en un archivo de configuración externo en lugar de código compilado de la aplicación.  
  
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administre eficazmente los elementos como referencias, conexiones de datos, carpetas y archivos necesarios para la tarea de desarrollo a través de soluciones y proyectos.  
  
 [Ampliación de otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] services para crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].