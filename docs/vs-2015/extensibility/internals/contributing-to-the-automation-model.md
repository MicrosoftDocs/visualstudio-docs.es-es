---
title: Contribución al modelo de automatización | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c84ea078f9b7c1268b765111cc400f6e51b783f1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998187"
---
# <a name="contributing-to-the-automation-model"></a>Contribución al modelo de automatización
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio proporciona un conjunto de interfaces de automatización para personalizar el entorno. El modelo de automatización es el modelo de objetos que permite a los usuarios finales crear extensiones y complementos de Visual Studio.  
  
 Además, es adecuado para usted, como desarrollador del VSPackage, contribuir al modelo de automatización; al hacerlo, habilita los usuarios finales de su VSPackage para crear complementos y por lo general proporcionan una experiencia de modelo de usuario coherente al usar el paquete de VS en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Para que el usuario final experiencia coherente, puede seguir un conjunto de directrices al diseñar el paquete de VS para que el modelo de automatización para el VSPackage sigue las ideas en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)  
 Define el modelo de automatización como grupos relacionados de objetos que controlan las facetas principales del entorno común. Este conjunto de objetos se muestra en un diagrama del modelo de automatización.  
  
 [Provisión de automatización de VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Describe las dos formas principales para proporcionar automatización para el VSPackage.  
  
 [Exposición de objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)  
 Proporciona instrucciones paso a paso para crear objetos específicos de VSPackage.  
  
 [Modelado de proyectos](../../extensibility/internals/project-modeling.md)  
 Explica los objetos de proyecto estándar que son necesarios para crear la automatización para el tipo de proyecto nuevo y se muestra la ruta de acceso que sigue la automatización de proyectos. En este tema también proporciona programas de declaraciones e implementación para las clases.  
  
 [Exposición de eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Proporciona instrucciones paso a paso para la creación de eventos para el modelo de automatización.  
  
 [Compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)  
 Describe cómo devolver un objeto de automatización para compatibilidad con propiedades de un paquete VSPackage personalizada del **opciones** cuadro de diálogo en el **herramienta** menú extendiendo el `DTE.Properties` objeto.  
  
 [Provisión de automatización para código](../../extensibility/internals/providing-automation-for-code.md)  
 Explica que no es necesario crear un modelo de automatización para el código. Sin embargo, se proporciona un vínculo de este tema se proporciona información muy precisos en los modelos de código.  
  
 [Cómo: Provisión de automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explica que la provisión de automatización es una buena idea cada vez que se desea disponer de los objetos de automatización en una ventana, y el entorno no ya proporciona un objeto de automatización listos para usar. Analiza la automatización de las ventanas de herramientas y ventanas de documento.  
  
 [Uso del modelo de automatización](../../extensibility/internals/using-the-automation-model.md)  
 Proporciona dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto inicial de objetos de automatización.  
  
 [Automatización para configuración y objetos SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Proporciona información sobre la automatización de las opciones de configuración y automatización para los elementos seleccionados.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Proporciona un ejemplo de código que muestra cómo un VSPackage participa en el modelo de objetos de automatización DTE. Las listas de parámetros, valores devueltos y comentarios seleccionadas.  
  
## <a name="related-sections"></a>Secciones relacionadas
