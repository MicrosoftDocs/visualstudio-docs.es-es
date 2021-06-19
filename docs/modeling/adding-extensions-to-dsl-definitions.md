---
title: Agregar extensiones a definiciones DSL
description: Obtenga información sobre cómo la extensión de definición de DSL le permite crear un paquete de extensiones en un lenguaje específico de dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d9f1c92ebb879517d497af41fe98cec4492bd95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384894"
---
# <a name="add-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL

La extensión de definición de DSL permite crear un paquete de extensiones en un lenguaje específico de dominio (DSL). La extensión DSL, que se encuentra en una extensión de integración de Visual Studio (VSIX), se puede instalar en el equipo de un usuario de la misma manera que un DSL. Las características adicionales se pueden habilitar y deshabilitar dinámicamente en tiempo de ejecución. Las DSL no tienen que diseñarse explícitamente para la extensión, y las extensiones se pueden diseñar más adelante, o por terceros, sin modificar el DSL extendido.

Las extensiones dsl pueden incluir las siguientes características:

- Propiedades de los elementos de presentación y modelo

- Decoradores para formas y conectores

- Clases, relaciones, formas y conectores

- Restricciones de validación

- Pestañas y elementos del cuadro de herramientas

Un usuario de un DSL extendido puede crear y guardar un modelo que contiene instancias de las características adicionales. Otros usuarios que han instalado la extensión adecuada pueden leer el modelo. Los usuarios que no han instalado la extensión no pueden usar las características adicionales, pero pueden actualizar y guardar un modelo sin perder las características adicionales.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también

- [Entradas blogs relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
