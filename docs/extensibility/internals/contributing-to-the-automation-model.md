---
title: "Que contribuyen al modelo de automatización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5907f540e5f81e26b7d184352e3c38531ec5da66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="contributing-to-the-automation-model"></a>Que contribuyen al modelo de automatización
Visual Studio proporciona un conjunto de interfaces de automatización para personalizar el entorno. El modelo de automatización es el modelo de objetos que permite a los usuarios finales crear extensiones y complementos de Visual Studio.  
  
 Además, es adecuado para usted, como desarrollador del VSPackage, contribuir al modelo de automatización; al hacerlo, permite que los usuarios finales del paquete de VS para crear complementos y suele ofrecer una experiencia coherente de modelo cuando utilicen el VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Para que el usuario final experiencia coherentes, puede seguir un conjunto de instrucciones cuando se diseña el VSPackage para que el modelo de automatización para el VSPackage sigue las ideas en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)  
 Define el modelo de automatización como relacionados a un grupo de objetos que controlan aspectos principales del entorno comunes. Este conjunto de objetos se ilustran en un diagrama del modelo de automatización.  
  
 [Provisión de automatización de VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Describe las dos formas principales para proporcionar la automatización para el VSPackage.  
  
 [Exposición de objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)  
 Proporciona instrucciones paso a paso para crear objetos específicos de VSPackage.  
  
 [Modelado de proyectos](../../extensibility/internals/project-modeling.md)  
 Explica los objetos de proyecto estándar que son necesarios para crear la automatización para el nuevo tipo de proyecto y muestra la ruta de acceso que sigue la automatización de proyecto. En este tema también proporciona las listas de declaraciones y la implementación de clases.  
  
 [Exponer eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Proporciona instrucciones paso a paso para la creación de eventos para el modelo de automatización.  
  
 [Compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)  
 Describe cómo devolver un objeto de automatización para compatibilidad con propiedades de un paquete VSPackage personalizado **opciones** cuadro de diálogo en el **herramienta** menú extendiendo la `DTE.Properties` objeto.  
  
 [Provisión de automatización para código](../../extensibility/internals/providing-automation-for-code.md)  
 Explica que no es necesario crear un modelo de automatización para el código. Sin embargo, se proporciona un vínculo de este tema proporciona información relevante en los modelos de código.  
  
 [Provisión de automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explica que proporciona automatización es una buena idea cada vez que se desea disponer de los objetos de automatización en una ventana y el entorno no ya proporciona un objeto de automatización listos para su uso. Analiza la automatización de las ventanas de herramientas y ventanas de documento.  
  
 [Uso del modelo de automatización](../../extensibility/internals/using-the-automation-model.md)  
 Proporciona dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto inicial de los objetos de automatización.  
  
 [Automatización para configuración y objetos SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Proporciona información sobre la automatización de las opciones de configuración y automatización para los elementos seleccionados.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Proporciona un ejemplo de código que muestra cómo un VSPackage participa en el modelo de objetos de automatización DTE. Muestra los parámetros, valores devueltos y comentarios seleccionados.  
  
## <a name="related-sections"></a>Secciones relacionadas