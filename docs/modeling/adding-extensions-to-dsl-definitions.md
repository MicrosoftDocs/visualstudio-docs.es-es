---
title: Agregar extensiones a definiciones DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9f39c45382fc55144f8200c3951fb4a229b7a43
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867376"
---
# <a name="add-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL

Extensión de la definición de DSL permite crear un paquete de extensiones para un lenguaje específico de dominio (DSL). La extensión DSL, que se encuentra en una extensión de integración de Visual Studio (VSIX), puede instalarse en el equipo del usuario en la misma manera que un DSL. Las características adicionales se pueden habilitar y deshabilitar en tiempo de ejecución dinámicamente. DSL no tiene que estar diseñado explícitamente para la extensión y las extensiones pueden diseñarse posterior, o por terceros, sin alterar el DSL extendido.

Extensiones DSL pueden incluir las siguientes características:

-   Propiedades de elementos de modelo y la presentación

-   Elementos Decorator para formas y conectores

-   Las clases, relaciones, formas y conectores

-   Restricciones de validación

-   Pestañas y elementos de cuadro de herramientas

Un usuario de un DSL extendido puede crear y guardar un modelo que contiene las instancias de las características adicionales. El modelo se puede leer por otros usuarios que tengan instalada la extensión adecuada. Los usuarios que no tengan instalada la extensión no pueden usar las características adicionales, pero puede actualizar y guardar un modelo sin perder las características adicionales.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también

- [Blogs relacionados](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
