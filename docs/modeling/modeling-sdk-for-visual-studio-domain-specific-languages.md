---
title: Modelar el SDK de Visual Studio - Lenguajes específicos de dominio
description: Aprenda a usar el SDK de modelado para Visual Studio, puede crear eficaces herramientas de desarrollo basadas en modelos que puede integrar en Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85deb6239360fc1c56ceb1ba4d23be02d6dbfd70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950390"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modelar el SDK de Visual Studio - Lenguajes específicos de dominio

Con el SDK de modelado para Visual Studio, puede crear eficaces herramientas de desarrollo basadas en modelos que puede integrar en Visual Studio. De la misma manera, puede crear una o más definiciones de modelo e integrarlas en un conjunto de herramientas.

En el núcleo de MSDK se encuentra la definición de un modelo creado para representar conceptos del área de negocio. Puede rodear el modelo con una variedad de herramientas, como una vista en forma de diagrama, la capacidad de generar código y otros artefactos, comandos para transformar el modelo y la capacidad de interactuar con código y otros objetos en Visual Studio. Al desarrollar el modelo, puede combinarlo con otros modelos y herramientas para formar un conjunto de herramientas eficaz centrado en el desarrollo.

MSDK permite desarrollar un modelo rápidamente en forma de lenguaje específico de dominio (DSL). Se comienza por usar un editor especializado para definir un esquema o sintaxis abstracta junto con una notación gráfica. A partir de esta definición, VMSDK genera:

- Una implementación del modelo con una API fuertemente tipada que se ejecuta en un almacén basado en transacciones.

- Un explorador basado en un árbol.

- Un editor gráfico en el que los usuarios pueden ver el modelo o las partes definidas de este.

- Métodos de serialización que guardan los modelos en XML legible.

- Medios para generar código de programa y otros artefactos mediante plantillas de texto.

Puede personalizar y ampliar todas estas características. Las extensiones se integran de modo que sigue siendo posible actualizar la definición de DSL y regenerar las características sin perder las extensiones.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Entradas blogs relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
