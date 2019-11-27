---
title: Extender diagramas de capas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301028"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede escribir código para crear y actualizar diagramas de capas y para validar la estructura del código del programa con diagramas de capas en Visual Studio. Puede agregar los comandos que aparecen en el menú contextual de los diagramas, personalizar gestos de arrastrar y colocar, así como obtener acceso al modelo de capas desde las plantillas de texto. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio (VSIX) y distribuirla a otros usuarios de Visual Studio.

 Para obtener más información sobre los diagramas de capas, vea:

- [Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)

- [Diagrama de capas: instrucciones](../modeling/layer-diagrams-guidelines.md)

- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

- [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> Requisitos
 Necesita tener instalado lo siguiente en el equipo donde desea desarrollar las extensiones de capa:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [SDK de modelado para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  Debe tener una versión adecuada de Visual Studio instalada en el equipo donde desea ejecutar las extensiones de capas. Para obtener más información, vea [implementar una extensión de modelo de capas](../modeling/deploy-a-layer-model-extension.md).

  Para ver las versiones de Visual Studio que admiten los diagramas de capas, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>Esta sección
 [Agregar comandos y gestos a diagramas de capas](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Agregar validación de arquitectura personalizada a diagramas de capas](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Agregar propiedades personalizadas a diagramas de capas](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Navegar y actualizar modelos de capas en el código del programa](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Implementar una extensión del modelo de capas](../modeling/deploy-a-layer-model-extension.md)

 [Solucionar problemas de extensiones de diagramas de capas](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Vea también
 [Definir e instalar una extensión de modelado](../modeling/define-and-install-a-modeling-extension.md) [diagramas de capas: referencia](../modeling/layer-diagrams-reference.md) [diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md) [crear diagramas de capas a partir](../modeling/create-layer-diagrams-from-your-code.md) del código [validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md) [generar archivos a partir de un modelo UML](../modeling/generate-files-from-a-uml-model.md) [abrir un modelo UML mediante la API de Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
