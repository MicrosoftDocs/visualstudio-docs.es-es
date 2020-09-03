---
title: Usar una búsqueda en el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63ad6f8b6d3afd1f30f2e9a02eaa4927fb3608d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817481"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Usar una búsqueda en el Diseñador de flujo de trabajo

Para facilitar la creación de flujos de trabajo más grandes y complejos, puede buscar en el Diseñador de flujo de trabajo para buscar elementos por palabra clave. Observe que el diseñador no admite Replace.

## <a name="quick-find"></a>Búsqueda rápida

Búsqueda rápida busca lo siguiente en el diseñador:

- Propiedades de los objetos <xref:System.Activities.Activity>, objetos <xref:System.Activities.Statements.FlowNode>, objetos <xref:System.Activities.Statements.State>, transiciones, así como otros elementos de control de flujo personalizados.

- Variables

- Argumentos

- Expresiones

### <a name="use-quick-find"></a>Usar búsqueda rápida

1. Con el diseñador de flujo de trabajo abierto, presione **Ctrl + F**o seleccione **Editar**  >  **Buscar y reemplazar**  >  **búsqueda rápida**.

2. Escriba el término de búsqueda en el cuadro de texto **Buscar** y haga clic en **Buscar siguiente**.

3. El término de búsqueda se encuentra en el flujo de trabajo actual. La siguiente imagen muestra un nombre para mostrar de la actividad que se encuentra en el diseñador:

   ![Resultado de la búsqueda en el Diseñador de flujo de trabajo](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Buscar en archivos

Buscar en archivos busca cadenas en archivos de flujo de trabajo, incluidos los archivos XAML.

### <a name="use-find-in-files"></a>Usar buscar en archivos

1. En Visual Studio, presione **Ctrl** + **MAYÚS** + **F**o seleccione **Editar**  >  **Buscar y reemplazar**  >  **Buscar en archivos**.

2. Escriba el elemento de búsqueda en el cuadro de texto **Buscar** y haga clic en **buscar todo**.

3. El resultado de la búsqueda se muestra en la vista resultado de la **búsqueda** . Al hacer doble clic en un elemento de resultado, navega a la actividad que contiene la coincidencia en el diseñador de flujo de trabajo.