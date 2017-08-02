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
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>Extender propiedades
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propiedades** ventana es un explorador de propiedades universal para los componentes COM y COM + y todos los admite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] productos. El **propiedades** ventana funciona con `ITypeInfo` escriba la información y los metadatos de COM + para mostrar las propiedades de tiempo de diseño para el objeto seleccionado actualmente en cualquier otra ventana en el entorno de desarrollo integrado (IDE).  
  
 El **propiedades** ventana, que se puede abrir presionando F4 del teclado o seleccionando **ventana propiedades** en el **vista** menú, se utiliza para ver y editar propiedades de tiempo de diseño independientes de la configuración y los eventos de los objetos seleccionados. Propiedades dependientes de la configuración, asociados con soluciones y proyectos, se muestran en [páginas de propiedades](../../extensibility/internals/property-pages.md). Para obtener más información, consulte [propiedades del proyecto: NIB](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [opciones de configuración de administración de](../../extensibility/internals/managing-configuration-options.md), y [NIB: Item Management in Projects](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Información general sobre la ventana de propiedades](~/extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Propiedades (ventana)  
  
 Esta sección proporciona información detallada que se relaciona con las áreas individuales de la **propiedades** ventana y las interfaces que debe implementar y llamada a rellenar la ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general sobre la ventana de propiedades](../../extensibility/internals/properties-window-overview.md)  
 Explica el propósito de la **propiedades** ventana en relación con la ventana de herramientas y la ventana de documento.  
  
 [Directiva de plantilla y la ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Describe cómo un proyecto se incluye en un proyecto de enterprise Templates y cómo ese proyecto de enterprise Templates puede aplicar directivas.  
  
 [Interfaces y campos de la ventana de propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica la base para la selección que determina qué información se muestra en el **propiedades** ventana.  
  
 [Lista de objetos de ventana de propiedades](../../extensibility/internals/properties-window-object-list.md)  
 Describe el propósito de la **propiedades** lista de objetos de ventana, que describe cómo, cuando un objeto diferente de esta lista desencadena una llamada, el entorno se informa que se ha seleccionado un nuevo objeto.  
  
 [Botones de la ventana de propiedades](../../extensibility/internals/properties-window-buttons.md)  
 Explica el propósito de los botones de cuatro predeterminados mostrados en la **propiedades** barra de herramientas.  
  
 [Mostrar cuadrícula de propiedades](../../extensibility/internals/properties-display-grid.md)  
 Explica dónde se encuentran los nombres de propiedad y los campos de valores de propiedad en la cuadrícula.  
  
 [Anuncio del seguimiento de selección de la ventana de propiedades](../../misc/announcing-property-window-selection-tracking.md)  
 Describe la selección de seguimiento para la **propiedades** ventana.  
  
 [Ocultar propiedades que tienen propiedades secundarias](../../misc/hiding-properties-that-have-child-properties.md)  
 Explica cómo ocultar las propiedades que tienen propiedades secundarias mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>interfaz.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [Proporcionar una ventana de propiedades personalizadas](../../misc/providing-a-custom-properties-window.md)  
 Detalla los pasos para proporcionar su propio explorador de propiedades.  
  
 [Obtener descripciones de los campos de la ventana Propiedades](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explica dónde encontrar el área de descripción que se muestra información relacionada con el campo de la propiedad seleccionada.  
  
 [Actualizar valores de propiedad en la ventana Propiedades](../../misc/updating-property-values-in-the-properties-window.md)  
 Proporciona instrucciones paso a paso que muestran las dos maneras de mantener el **propiedades** ventana sincronizada con los cambios de valor de propiedad.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe los proyectos como bloques de creación de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)  
 Describe cómo se puede utilizar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plataforma para probar y depurar aplicaciones que se crean continuamente.  
  
 [Propiedades del documento HTML, ventana Propiedades](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Proporciona instrucciones para editar un documento HTML directamente desde la ventana Propiedades y proporciona una tabla que detalla los campos de un documento HTML en la ventana Propiedades.  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Describe el `IDispatch` interfaz, que primero se diseñó para admitir la automatización, que proporciona un mecanismo de tiempo de ejecución para tener acceso y recuperar información acerca de los métodos y propiedades de un objeto.  
  
 [NIB: Introducción a las propiedades dinámicas (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Proporciona una visión general de las propiedades dinámicas que permiten configurar la aplicación para que los valores de propiedad se almacenan en un archivo de configuración externo en lugar de código compilado de la aplicación.  
  
 [NIB: proyectos como contenedores](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Describe el rol del proyecto como un contenedor de una solución para administrar, compilar y depurar los elementos que conforman la aplicación lógica.  
  
 [Propiedades del proyecto: NIB](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Describe cómo el proyecto administra configuraciones que permiten las propiedades de control que se aplican a todo el proyecto y también las propiedades que están limitadas a ciertas configuraciones de compilación del proyecto.  
  
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administra con eficacia los elementos como referencias, conexiones de datos, carpetas y archivos necesarios para el desarrollo a través de soluciones y proyectos.  
  
 [Extensión de otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servicios para crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
