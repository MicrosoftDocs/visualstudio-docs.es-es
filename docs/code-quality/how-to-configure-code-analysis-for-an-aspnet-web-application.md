---
title: Configurar análisis de código de aplicación Web de ASP.NET
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 51638db2cf258cc1a91c659c137c6a17811fa8c8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820702"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Procedimiento Configurar el análisis de código para una aplicación web ASP.NET

En Visual Studio, puede seleccionar entre una lista de análisis de código *conjuntos de reglas* para aplicar a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación web. El conjunto de reglas predeterminado es Reglas mínimas recomendadas de Microsoft. Puede seleccionar otro conjunto de reglas para aplicar al sitio web.

1. Seleccione el sitio web en **el Explorador de soluciones**.

2. En el **analizar** menú, haga clic en **configurar análisis de código para el sitio Web**.

3. Si ha seleccionado la solución y la solución tiene más de un proyecto, seleccione el sistema de operativo de configuración y de destino de compilación desde el **configuración** y **plataforma** enumera.

4. Para cada proyecto de la solución, haga clic en el **Pravidel** columna y, a continuación, haga clic en el nombre de la regla de configuración para ejecutar.

5. De forma predeterminada, el análisis de código se ejecuta en todos los proyectos de la solución. Para deshabilitar o habilitar el análisis de código para un proyecto determinado, siga estos pasos:

    1. Haga clic en el nombre del proyecto y, a continuación, haga clic en Propiedades.

    2. Active o desactive el **Habilitar análisis de código** casilla de verificación. También puede ejecutar análisis de código seleccionando **ejecutar análisis de código en el sitio Web** desde el **analizar** menú.

6. En el **ejecutar este conjunto de reglas** desplegable lista, siga estos pasos:

    - Seleccione el conjunto de reglas que desea usar.

    - Seleccione  **\<examinar >** especificar una regla personalizada existente conjunto que no está en la lista.

    - Definir un [conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md).