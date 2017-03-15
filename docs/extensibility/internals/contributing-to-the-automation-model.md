---
title: "Que contribuyen al modelo de automatizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "automatización [Visual Studio SDK]"
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Que contribuyen al modelo de automatizaci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio proporciona un conjunto de interfaces de automatización para personalizar el entorno. El modelo de automatización es el modelo de objetos que permite a los usuarios finales crear extensiones y complementos de Visual Studio.  
  
 Además, es adecuado para usted, como desarrollador VSPackage, contribuir al modelo de automatización; al hacerlo, permite a los usuarios de su paquete VSPackage para crear complementos y generalmente proporcionan una experiencia de usuario coherente modelo cuando usen su VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Para que el usuario final experiencia coherente, puede seguir un conjunto de directrices que diseñar el VSPackage para que el modelo de automatización para el VSPackage sigue las ideas en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## En esta sección  
 [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)  
 Define el modelo de automatización como grupos relacionados de objetos que controlan aspectos principales del entorno común. Este conjunto de objetos se representa en un diagrama del modelo de automatización.  
  
 [Automatización de VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Describe las dos formas principales para proporcionar automatización para el VSPackage.  
  
 [Exponer objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)  
 Proporciona instrucciones paso a paso para crear objetos específicos de VSPackage.  
  
 [Modelo de proyecto](../../extensibility/internals/project-modeling.md)  
 Explica los objetos de proyecto estándar que son necesarios para crear la automatización para el tipo de proyecto nuevo y muestra la ruta de acceso que sigue la automatización de proyectos. En este tema también proporciona listas de declaraciones y la implementación de clases.  
  
 [Exponer eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Proporciona instrucciones paso a paso para la creación de eventos para el modelo de automatización.  
  
 [Compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)  
 Describe cómo devolver un objeto de automatización para compatibilidad con propiedades de un paquete VSPackage personalizada del **opciones** cuadro de diálogo en el **herramienta** menú extendiendo la `DTE.Properties` objeto.  
  
 [Automatización de código](../../extensibility/internals/providing-automation-for-code.md)  
 Explica que no es necesario crear un modelo de automatización para el código. Sin embargo, se proporciona un vínculo de este tema proporciona información perspicaz en modelos de código.  
  
 [Cómo: proporcionar automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explica que la automatización es una buena idea siempre que desee disponer de los objetos de automatización en una ventana y el entorno no proporciona un objeto de automatización predefinidos ya. Analiza la automatización para ventanas de herramientas y ventanas de documento.  
  
 [Utilizando el modelo de automatización](../../extensibility/internals/using-the-automation-model.md)  
 Proporciona dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto inicial de objetos de automatización.  
  
 [Automatización para la configuración y objetos SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Proporciona información acerca de automatización para las opciones de configuración y automatización para los elementos seleccionados.  
  
## Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Proporciona un ejemplo de código que muestra cómo un VSPackage participa en el modelo de objetos de automatización DTE. Listas de parámetros, valores devueltos y comentarios seleccionados.  
  
## Secciones relacionadas