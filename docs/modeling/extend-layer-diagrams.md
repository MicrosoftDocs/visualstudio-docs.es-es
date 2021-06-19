---
title: Ampliar diagramas de dependencia
description: Obtenga información sobre cómo escribir código para crear y actualizar diagramas de dependencias y cómo validar la estructura del código del programa con los diagramas de dependencias de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2ed8700cfb18aacf41464bfdfacaedac557bb00
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388911"
---
# <a name="extend-dependency-diagrams"></a>Ampliar diagramas de dependencia

Puede escribir código para crear y actualizar diagramas de dependencias y para validar la estructura del código del programa con los diagramas de dependencias de Visual Studio. Puede agregar los comandos que aparecen en el menú contextual de los diagramas, personalizar gestos de arrastrar y colocar, así como obtener acceso al modelo de capas desde las plantillas de texto. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio (VSIX) y distribuirla a otros usuarios de Visual Studio.

## <a name="requirements"></a>Requisitos

Necesita tener instalado lo siguiente en el equipo donde desea desarrollar las extensiones de capa:

- Programa para la mejora

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- SDK de modelado para Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Debe tener una edición adecuada de Visual Studio instalado en el equipo donde desea ejecutar las extensiones de capa. Para ver qué ediciones de Visual Studio admiten diagramas de dependencias, consulte Compatibilidad de edición [con herramientas de arquitectura y modelado.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="see-also"></a>Vea también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)
- [Crear diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
- [Validación código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)
