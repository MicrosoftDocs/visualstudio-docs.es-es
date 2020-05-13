---
title: Ampliar diagramas de dependencia
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301492"
---
# <a name="extend-dependency-diagrams"></a>Ampliar diagramas de dependencia

Puede escribir código para crear y actualizar diagramas de dependencia y para validar la estructura del código del programa con los diagramas de dependencia en Visual Studio. Puede agregar los comandos que aparecen en el menú contextual de los diagramas, personalizar gestos de arrastrar y colocar, así como obtener acceso al modelo de capas desde las plantillas de texto. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio (VSIX) y distribuirla a otros usuarios de Visual Studio.

## <a name="requirements"></a>Requisitos

Necesita tener instalado lo siguiente en el equipo donde desea desarrollar las extensiones de capa:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- SDK de modelado para Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Debe tener una edición adecuada de Visual Studio instalada en el equipo donde desea ejecutar las extensiones de capa. Para ver qué ediciones de Visual Studio admiten diagramas de dependencia, vea Compatibilidad con edition para herramientas de [arquitectura y modelado.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="see-also"></a>Consulte también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)
- [Crear diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
- [Validación código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)
