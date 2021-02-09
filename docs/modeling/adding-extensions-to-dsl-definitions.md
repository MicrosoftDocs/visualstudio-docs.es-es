---
title: Agregar extensiones a definiciones DSL
description: Obtenga información sobre cómo la extensión de definición de DSL le permite crear un paquete de extensiones para un lenguaje específico del dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1208c152534206a0ed2894fc0e41d844e0b77d47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861964"
---
# <a name="add-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL

La extensión DSL Definition le permite crear un paquete de extensiones para un lenguaje específico del dominio (DSL). La extensión DSL, que se encuentra en una extensión de integración de Visual Studio (VSIX), se puede instalar en el equipo de un usuario de la misma manera que un DSL. Las características adicionales se pueden habilitar y deshabilitar dinámicamente en tiempo de ejecución. Los DSL no tienen que diseñarse explícitamente para la extensión, y las extensiones se pueden diseñar posteriormente, o por parte de terceros, sin modificar el DSL extendido.

Las extensiones DSL pueden incluir las siguientes características:

- Propiedades de los elementos de modelo y presentación

- Elementos Decorator para formas y conectores

- Clases, relaciones, formas y conectores

- Restricciones de validación

- Elementos y pestañas del cuadro de herramientas

Un usuario de un DSL extendido puede crear y guardar un modelo que contenga instancias de las características adicionales. El modelo lo pueden leer otros usuarios que hayan instalado la extensión adecuada. Los usuarios que no han instalado la extensión no pueden usar las características adicionales, pero pueden actualizar y guardar un modelo sin perder las características adicionales.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también

- [Entradas blogs relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
