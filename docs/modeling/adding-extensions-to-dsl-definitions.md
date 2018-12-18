---
title: Agregar extensiones a definiciones DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc764df3037baeba36666ce896549018d86c2a21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947539"
---
# <a name="add-extensions-to-dsl-definitions"></a>Agregar extensiones a las definiciones de DSL

Extensión de definición DSL permite crear un paquete de extensiones en un lenguaje específico de dominio (DSL). La extensión DSL, que se encuentra en una extensión de integración de Visual Studio (VSIX), se puede instalar en el equipo del usuario de la misma manera que un DSL. Las características adicionales se pueden habilitar y deshabilitar en tiempo de ejecución de dinámicamente. DSL no tienen que diseñarse explícitamente para la extensión y extensiones pueden diseñarse posterior, o por terceros, sin alterar el ADSL extendido.

Extensiones DSL pueden incluir las siguientes características:

-   Propiedades de elementos de modelo y la presentación

-   Decoradores para formas y conectores

-   Las clases, relaciones, formas y conectores

-   Restricciones de validación

-   Pestañas y elementos de cuadro de herramientas

Un usuario de un DSL extendido puede crear y guardar un modelo que contiene las instancias de las características adicionales. El modelo se puede leer por otros usuarios que tengan instalada la extensión adecuada. Los usuarios que no se han instalado la extensión no pueden usar las características adicionales, pero puede actualizar y guardar un modelo sin perder las características adicionales.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también

- [Blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
