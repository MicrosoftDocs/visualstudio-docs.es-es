---
title: Extender propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59afc6a95e327460602ece8db58f075b483d0e09
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995890"
---
# <a name="extending-properties"></a>Extensión de propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **propiedades** ventana es un explorador de propiedades universal para los componentes COM y COM + y admite todas [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] productos. El **propiedades** ventana funciona con `ITypeInfo` escriba la información y los metadatos de COM + para enumerar las propiedades de tiempo de diseño para el objeto seleccionado actualmente en otra ventana en el entorno de desarrollo integrado (IDE).  
  
 El **propiedades** ventana, que se puede abrir presionando F4 en el teclado, o bien seleccionando **ventana propiedades** en el **vista** menú, se utiliza para ver y editar propiedades de tiempo de diseño independientes de la configuración y los eventos de los objetos seleccionados. Propiedades dependientes de la configuración, asociadas con soluciones y proyectos, se muestran en [páginas de propiedades](../../extensibility/internals/property-pages.md). Para obtener más información, consulte [las propiedades del proyecto: NIB](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md), y [NIB: administración elementos en proyectos](http://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Información general sobre la ventana de propiedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Propiedades (ventana)  
  
 Esta sección proporciona información detallada relacionada con las áreas individuales de la **propiedades** ventana y las interfaces que debe implementar y llamada a rellenar la ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general sobre la ventana Propiedades](../../extensibility/internals/properties-window-overview.md)  
 Explica el propósito de la **propiedades** ventana con respecto a la ventana de herramientas y la ventana de documento.  
  
 [Directiva de plantilla y ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Describe cómo un proyecto se encuentra en una plantilla de proyecto y cómo esa plantilla de proyecto puede aplicar directivas.  
  
 [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica la base para la selección que determina qué información se muestra en el **propiedades** ventana.  
  
 [Lista de objetos de la ventana Propiedades](../../extensibility/internals/properties-window-object-list.md)  
 Describe el propósito de la **propiedades** lista de objetos de ventana, que describe cómo hacerlo, cuando un objeto diferente de esta lista desencadena una llamada, el entorno se informa que se ha seleccionado un nuevo objeto.  
  
 [Botones de la ventana Propiedades](../../extensibility/internals/properties-window-buttons.md)  
 Explica el propósito de los botones de cuatro predeterminados mostrados en la **propiedades** barra de herramientas de ventana.  
  
 [Cuadrícula para mostrar de Propiedades](../../extensibility/internals/properties-display-grid.md)  
 Explica dónde se encuentran los nombres de propiedad y los campos de valores de propiedad en la cuadrícula.  
  
 [Anuncio del seguimiento de selección de la ventana de propiedades](../../misc/announcing-property-window-selection-tracking.md)  
 Describe la selección de seguimiento para el **propiedades** ventana.  
  
 [Ocultar propiedades que tienen propiedades secundarias](../../misc/hiding-properties-that-have-child-properties.md)  
 Explica cómo ocultar las propiedades que tienen propiedades secundarias mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interfaz.  
  
 [Proporcionar una ventana de propiedades personalizadas](../../misc/providing-a-custom-properties-window.md)  
 Se detallan los pasos para proporcionar su propio explorador de propiedades.  
  
 [Obtener descripciones de los campos de la ventana Propiedades](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explica dónde se encuentra el área de descripción que muestra información relacionada con el campo de la propiedad seleccionada.  
  
 [Actualizar valores de propiedad en la ventana Propiedades](../../misc/updating-property-values-in-the-properties-window.md)  
 Proporciona instrucciones paso a paso que muestran las dos maneras de mantener el **propiedades** ventana sincronizada con los cambios de valor de propiedad.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe los proyectos como los bloques de creación de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)  
 Describe cómo puede usar el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plataforma para probar y depurar aplicaciones como proceso de compilación continuamente.  
  
 [Propiedades del documento HTML, ventana Propiedades](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Proporciona instrucciones para editar un documento HTML directamente desde la ventana Propiedades y proporciona una tabla que detalla los campos de un documento HTML en la ventana Propiedades.  
  
 [IDispatch](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Describe el `IDispatch` interfaz, que primero se diseñó para admitir la automatización, que proporciona un mecanismo de tiempo de ejecución para acceder y recuperar información acerca de los métodos y propiedades de un objeto.  
  
 [NIB: Introducción a las propiedades dinámicas (Visual Studio)](http://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Proporciona información general de las propiedades dinámicas que permiten configurar la aplicación para que los valores de propiedad se almacenan en un archivo de configuración externo en lugar de código compilado de la aplicación.  
  
 [NIB: proyectos como contenedores](http://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Describe el rol del proyecto como un contenedor en una solución para administrar, compilar y depurar los elementos que componen la aplicación lógica.  
  
 [Propiedades del proyecto: NIB](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Describe cómo el proyecto administra la configuración que permiten las propiedades de control que se aplican a todo el proyecto y también las propiedades que están limitadas a determinadas configuraciones de compilación del proyecto.  
  
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica cómo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] administra con eficacia los elementos como las referencias, las conexiones de datos, carpetas y archivos necesarios para el desarrollo a través de soluciones y proyectos.  
  
 [Ampliación de otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar los servicios de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para crear elementos de interfaz de usuario que coincidan con el resto de servicios de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
