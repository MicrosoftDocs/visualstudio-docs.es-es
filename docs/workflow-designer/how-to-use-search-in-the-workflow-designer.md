---
title: Filtrar Usar una búsqueda en el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b1d29c4398e6b6c377ab493c495951f942d15965
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942393"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Filtrar Usar una búsqueda en el Diseñador de flujo de trabajo

Para facilitar la creación de flujos de trabajo más grandes y complejas, puede buscar dentro del Diseñador de flujo de trabajo para buscar elementos por palabra clave. Observe que el diseñador no admite Replace.

## <a name="quick-find"></a>Búsqueda rápida

Búsqueda rápida busca lo siguiente en el diseñador:

-   Propiedades de los objetos <xref:System.Activities.Activity>, objetos <xref:System.Activities.Statements.FlowNode>, objetos <xref:System.Activities.Statements.State>, transiciones, así como otros elementos de control de flujo personalizados.

-   Variables

-   Argumentos

-   Expresiones

### <a name="use-quick-find"></a>Usar la búsqueda rápida

1. Con el Diseñador de flujo de trabajo abierto, presione **CTRL+f**, o bien seleccione **editar** > **buscar y reemplazar** > **búsqueda rápida**.

2. Escriba el término de búsqueda en el **buscar** cuadro de texto y haga clic en **Buscar siguiente**.

3. El término de búsqueda se encuentra en el flujo de trabajo actual. La siguiente imagen muestra el nombre para mostrar una actividad que se encuentra en el diseñador:

   ![Resultado de la búsqueda en el Diseñador de flujo de trabajo](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Buscar en archivos

Buscar en archivos busca cadenas en archivos de flujo de trabajo, incluidos los archivos XAML.

### <a name="use-find-in-files"></a>Usar la función Buscar en archivos

1.  En Visual Studio, presione **Ctrl**+**MAYÚS**+**F**, o bien seleccione **editar**  >   **Buscar y reemplazar** > **buscar en archivos**.

2.  Escriba el elemento de búsqueda en el **buscar** cuadro de texto y haga clic en **Buscar todo**.

3.  Resultado de la búsqueda se muestra en el **resultado de la búsqueda** vista. Haga doble clic en un elemento de resultado se desplaza a la actividad que contiene a la coincidencia en el Diseñador de flujo de trabajo.