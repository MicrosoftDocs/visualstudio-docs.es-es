---
title: Contribución al modelo de automatización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ebe9a3d1c314a8e3b15ae7588f38abfd50518d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910741"
---
# <a name="contribute-to-the-automation-model"></a>Contribuir al modelo de automatización
Visual Studio proporciona un conjunto de interfaces de automatización para personalizar el entorno. El modelo de automatización es el modelo de objetos que permite a los usuarios finales crear extensiones y complementos de Visual Studio.

 Además, es adecuado para usted, como desarrollador del VSPackage, contribuir al modelo de automatización; al hacerlo, habilita los usuarios finales de su VSPackage para crear complementos y por lo general proporcionan una experiencia de modelo de usuario coherente al usar el paquete de VS en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Para que el usuario final experiencia coherente, puede seguir un conjunto de directrices al diseñar el paquete de VS para que el modelo de automatización para el VSPackage sigue las ideas en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>En esta sección
- [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)

 Define el modelo de automatización como grupos relacionados de objetos que controlan las facetas principales del entorno común. Este conjunto de objetos se muestra en un diagrama del modelo de automatización.

- [Proporcionar la automatización de VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Describe las dos formas principales para proporcionar automatización para el VSPackage.

- [Exponer objetos del proyecto](../../extensibility/internals/exposing-project-objects.md)

 Proporciona instrucciones paso a paso para crear objetos específicos de VSPackage.

- [Modelado de proyectos](../../extensibility/internals/project-modeling.md)

 Explica los objetos de proyecto estándar que son necesarios para crear la automatización para el tipo de proyecto nuevo y se muestra la ruta de acceso que sigue la automatización de proyectos. En este tema también proporciona programas de declaraciones e implementación para las clases.

- [Exponer eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Proporciona instrucciones paso a paso para la creación de eventos para el modelo de automatización.

- [Automatización de la compatibilidad con páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)

 Describe cómo devolver un objeto de automatización para compatibilidad con propiedades de un paquete VSPackage personalizada del **opciones** cuadro de diálogo en el **herramienta** menú extendiendo el `DTE.Properties` objeto.

- [Provisión de automatización para código](../../extensibility/internals/providing-automation-for-code.md)

 Explica que no es necesario crear un modelo de automatización para el código. Sin embargo, se proporciona un vínculo de este tema se proporciona información muy precisos en los modelos de código.

- [Cómo: Provisión de automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Explica que la provisión de automatización es una buena idea cada vez que se desea disponer de los objetos de automatización en una ventana, y el entorno no ya proporciona un objeto de automatización listos para usar. Analiza la automatización de las ventanas de herramientas y ventanas de documento.

- [Usar el modelo de automatización](../../extensibility/internals/using-the-automation-model.md)

 Proporciona dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto inicial de objetos de automatización.

- [Automatización de los objetos de configuración y SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Proporciona información sobre la automatización para objetos de configuración y SelectedItems.

## <a name="reference"></a>Referencia
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Proporciona un ejemplo de código que muestra cómo un VSPackage participa en el modelo de objetos de automatización DTE. Las listas de parámetros, valores devueltos y comentarios seleccionadas.
