---
title: Ampliar diagramas de dependencia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 304e1fe6356768ae5243ae38748d920444be41e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="extend-dependency-diagrams"></a>Ampliar diagramas de dependencia
Puede escribir código para crear y actualizar diagramas de dependencia y para validar la estructura del código del programa con diagramas de dependencia en Visual Studio. Puede agregar los comandos que aparecen en el menú contextual de los diagramas, personalizar gestos de arrastrar y colocar, así como obtener acceso al modelo de capas desde las plantillas de texto. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio (VSIX) y distribuirla a otros usuarios de Visual Studio.

 Para obtener más información acerca de los diagramas de dependencia, vea:

-   [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)

-   [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)

-   [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

-   [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)

##  <a name="prereqs"></a> Requisitos
 Necesita tener instalado lo siguiente en el equipo donde desea desarrollar las extensiones de capa:

-   Programa para la mejora

-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

-   Modelado del SDK para Visual Studio


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 Debe tener una versión adecuada de Visual Studio instalada en el equipo donde desea ejecutar las extensiones de capas. Para obtener más información, consulte [implementar una extensión de modelo de capas](../modeling/deploy-a-layer-model-extension.md).

 Para ver qué versiones de Visual Studio admiten diagramas de dependencia, vea [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>En esta sección
 [Adición de comandos y gestos a diagramas de dependencia](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Adición de validación de arquitectura personalizada a diagramas de dependencia](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Adición de propiedades personalizadas a diagramas de dependencia](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Navegar y actualizar modelos de capas en el código del programa](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Implementar una extensión del modelo de capas](../modeling/deploy-a-layer-model-extension.md)

 [Solución de problemas de extensiones para diagramas de dependencia](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Vea también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)
- [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
- [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)
