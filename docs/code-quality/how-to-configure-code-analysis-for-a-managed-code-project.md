---
title: Configurar el análisis de código
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431357"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Cómo: Configurar el análisis heredado para el código administrado

En Visual Studio, puede elegir entre una lista de [conjuntos](../code-quality/rule-set-reference.md) de reglas de análisis de código para aplicar a un proyecto de código administrado. De forma predeterminada, el conjunto de reglas **de reglas mínimas recomendadas** de Microsoft está seleccionado, pero puede aplicar un conjunto de reglas diferente si lo desea. Los conjuntos de reglas se pueden aplicar a uno o varios proyectos de una solución.

> [!NOTE]
> Este artículo se aplica al análisis heredado y no a los analizadores de [código basados en .NET Compiler Platform.](use-roslyn-analyzers.md)

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurar un conjunto de reglas para un proyecto de .NET Framework

1. Abra la pestaña **Análisis** de código en las páginas de propiedades del proyecto. Esto se puede lograr de una de las siguientes maneras:

   - En **el Explorador**de soluciones , seleccione el proyecto. En la barra de menús, seleccione **Analizar análisis** > **Configure Code Analysis** > de código de configuración**para \<nombre de proyecto>**.

   - Haga clic con el botón secundario en el proyecto en el **Explorador** de soluciones y seleccione **Propiedades**y, a continuación, seleccione la pestaña **Análisis** de código.

2. En las listas **Configuración** y **Plataforma,** seleccione la configuración de compilación y la plataforma de destino.

::: moniker range="vs-2017"

3. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione **Habilitar análisis**de código en compilación . También puede ejecutar el análisis de código manualmente seleccionando **Analizar** > **análisis \< **de código de ejecución de**análisis** > de código de ejecución en nombre de proyecto>.

::: moniker-end

::: moniker range=">=vs-2019"

3. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione **Ejecutar en compilación** en la sección **Analizadores binarios.** También puede ejecutar el análisis de código heredado manualmente, consulte [Cómo: Ejecutar análisis](how-to-run-legacy-code-analysis-manually-for-managed-code.md) de código heredado manualmente para código administrado para obtener más detalles.

::: moniker-end

4. Para ver las advertencias del código generado, desactive la casilla **Suprimir resultados del código generado.**

    > [!NOTE]
    > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla, y no se sobrescribirá.

::: moniker range="vs-2017"

5. En la lista Ejecutar este conjunto de **reglas,** realice una de las siguientes acciones:

::: moniker-end

::: moniker range=">=vs-2019"

5. En la lista **Reglas activas,** realice una de las siguientes acciones:

::: moniker-end

   - Seleccione el conjunto de reglas que desea utilizar.

   - Seleccione ** \<Examinar>** para buscar un conjunto de reglas personalizado existente que no esté en la lista.

   - Defina un conjunto de [reglas personalizado.](../code-quality/how-to-create-a-custom-rule-set.md)

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Especificar conjuntos de reglas para varios proyectos en una solución

De forma predeterminada, a todos los proyectos administrados de una solución se les asigna el conjunto de reglas de análisis de código *de reglas mínimas recomendadas* de Microsoft. Puede cambiar los conjuntos de reglas asignados a los proyectos de una solución en el cuadro de diálogo **Propiedades** de la solución.

1. Abra la solución en Visual Studio.

2. En el menú **Analizar** , seleccione Configurar análisis de **código para solución**.

3. Si es necesario, expanda **Propiedades comunes**y, a continuación, seleccione Configuración de **análisis**de código .

4. Puede especificar un conjunto de reglas para uno o varios proyectos:

    - Para especificar un conjunto de reglas para un proyecto individual, seleccione el nombre del proyecto.

    - Para especificar un conjunto de reglas para varios proyectos, mantenga pulsada la **tecla Ctrl** y seleccione los nombres de proyecto.

    - Para especificar todos los proyectos de la solución, mantenga pulsada la tecla **Mayús** y haga clic en la lista de proyectos.

5. Seleccione el campo **Conjunto** de reglas de un proyecto y, a continuación, seleccione el nombre del conjunto de reglas que desea aplicar.

## <a name="see-also"></a>Consulte también

- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)
