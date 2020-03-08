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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410248"
---
# <a name="extend-dependency-diagrams"></a>Ampliar diagramas de dependencia

Puede escribir código para crear y actualizar diagramas de dependencia y para validar la estructura del código del programa con diagramas de dependencia en Visual Studio. Puede agregar los comandos que aparecen en el menú contextual de los diagramas, personalizar gestos de arrastrar y colocar, así como obtener acceso al modelo de capas desde las plantillas de texto. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio (VSIX) y distribuirla a otros usuarios de Visual Studio.

## <a name="requirements"></a>Requisitos

Necesita tener instalado lo siguiente en el equipo donde desea desarrollar las extensiones de capa:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- SDK de modelado para Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Debe tener una edición adecuada de Visual Studio instalada en el equipo en el que desea ejecutar las extensiones de capa. Para ver qué ediciones de Visual Studio admiten diagramas de dependencia, vea [compatibilidad de la edición con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Consulte también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)
- [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
- [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)
