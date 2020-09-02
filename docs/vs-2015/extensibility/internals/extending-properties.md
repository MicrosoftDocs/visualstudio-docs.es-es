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
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690990"
---
# <a name="extending-properties"></a>Extensión de propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ventana **propiedades** es un explorador de propiedades universal para componentes com y com+ y admite todos los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] productos. La ventana **propiedades** funciona con `ITypeInfo` información de tipos y metadatos de com+ para mostrar las propiedades en tiempo de diseño para el objeto seleccionado actualmente en cualquier otra ventana del entorno de desarrollo integrado (IDE).  
  
 La ventana **propiedades** , que se puede abrir presionando F4 en el teclado o seleccionando la **ventana Propiedades** en el menú **Ver** , se usa para ver y editar propiedades y eventos de tiempo de diseño independientes de la configuración y de los objetos seleccionados. Las propiedades dependientes de la configuración, asociadas a soluciones y proyectos, se muestran en [las páginas de propiedades](../../extensibility/internals/property-pages.md). Para obtener más información, vea [NIB: propiedades del proyecto](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)y [NIB: administración de elementos en proyectos](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Información general sobre la ventana Propiedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Propiedades (ventana)  
  
 En esta sección se proporciona información detallada relacionada con las áreas individuales de la ventana **propiedades** y las interfaces que debe implementar y llamar a para rellenar la ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general sobre la ventana Propiedades](../../extensibility/internals/properties-window-overview.md)  
 Explica el propósito de la ventana **propiedades** con respecto a la ventana de herramientas y la ventana de documento.  
  
 [Directiva de plantilla y ventana Propiedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Describe el modo en que un proyecto se encuentra en un proyecto de plantilla de Enterprise y cómo puede aplicar la Directiva ese proyecto de Enterprise Templates.  
  
 [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica la base para la selección que determina qué información se muestra en la ventana **propiedades** .  
  
 [Lista de objetos de la ventana Propiedades](../../extensibility/internals/properties-window-object-list.md)  
 Describe el propósito de la lista de objetos de la ventana **propiedades** , que describe cómo, cuando un objeto diferente de esta lista desencadena una llamada, se informa al entorno de que se ha seleccionado un nuevo objeto.  
  
 [Botones de la ventana Propiedades](../../extensibility/internals/properties-window-buttons.md)  
 Explica el propósito de los cuatro botones predeterminados que se muestran en la barra de herramientas de la ventana **propiedades** .  
  
 [Cuadrícula para mostrar de Propiedades](../../extensibility/internals/properties-display-grid.md)  
 Explica dónde se encuentran los campos nombres de propiedad y valores de propiedad en la cuadrícula.  
  
 [Anuncio del seguimiento de selección de la ventana de propiedades](../../misc/announcing-property-window-selection-tracking.md)  
 Describe el seguimiento de la selección de la ventana **propiedades** .  
  
 [Ocultar propiedades que tienen propiedades secundarias](../../misc/hiding-properties-that-have-child-properties.md)  
 Explica cómo ocultar las propiedades que tienen propiedades secundarias implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interfaz.  
  
 [Proporcionar una ventana de propiedades personalizadas](../../misc/providing-a-custom-properties-window.md)  
 Detalla los pasos para proporcionar su propio explorador de propiedades.  
  
 [Obtener descripciones de los campos de la ventana Propiedades](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explica dónde encontrar el área de descripción que muestra información relacionada con el campo de propiedad seleccionado.  
  
 [Actualizar valores de propiedad en la ventana Propiedades](../../misc/updating-property-values-in-the-properties-window.md)  
 Proporciona instrucciones paso a paso que muestran las dos maneras de mantener la ventana **propiedades** sincronizada con los cambios de valores de propiedad.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe los proyectos como los bloques de creación del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)  
 Describe cómo se puede usar la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plataforma para probar y depurar aplicaciones continuamente a medida que se crean.  
  
 [Propiedades del documento HTML, Propiedades (Ventana)](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Proporciona instrucciones para editar un documento HTML directamente desde el ventana Propiedades y proporciona una tabla que detalla los campos de un documento HTML en el ventana Propiedades.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Describe la `IDispatch` interfaz, que se diseñó primero para admitir la automatización, proporcionando un mecanismo enlazado en tiempo de ejecución para obtener acceso y recuperar información sobre los métodos y las propiedades de un objeto.  
  
 [NIB: Introducción a las propiedades dinámicas (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Proporciona información general sobre las propiedades dinámicas que permiten configurar la aplicación para que los valores de propiedad se almacenen en un archivo de configuración externo en lugar de en el código compilado de la aplicación.  
  
 [NIB: proyectos como contenedores](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Describe el rol del proyecto como un contenedor en una solución para administrar, compilar y depurar lógicamente los elementos que componen la aplicación.  
  
 [NIB: propiedades del proyecto](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Describe cómo el proyecto administra la configuración que permite controlar las propiedades que se aplican a todo el proyecto y también a las propiedades que están limitadas a determinadas configuraciones de compilación del proyecto.  
  
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica cómo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] administra de forma eficaz los elementos como referencias, conexiones de datos, carpetas y archivos requeridos por el esfuerzo de desarrollo a través de soluciones y proyectos.  
  
 [Ampliación de otras partes de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar los servicios de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para crear elementos de interfaz de usuario que coincidan con el resto de servicios de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
