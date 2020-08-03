---
title: Configurar el análisis de código
ms.date: 04/04/2018
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
- vs.codeanalysis.propertypages.asp
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 985f14446f17d1a4df3cfd14e156f21b7a7ce0de
ms.sourcegitcommit: e359b93c93c6ca316c0d8b86c2b6e566171fd1ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507864"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Cómo: configurar el análisis heredado para código administrado

En Visual Studio, puede elegir en una lista de [conjuntos de reglas](../code-quality/rule-set-reference.md) de análisis de código para aplicarlos a un proyecto de código administrado. De forma predeterminada, se selecciona el conjunto de reglas **reglas mínimas recomendadas de Microsoft** , pero puede aplicar un conjunto de reglas diferente si lo desea. Los conjuntos de reglas se pueden aplicar a uno o varios proyectos de una solución.

> [!NOTE]
> Este artículo se aplica al análisis heredado y no a los [analizadores de código basados en .net Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurar un conjunto de reglas para un proyecto de .NET Framework

1. Abra la pestaña **análisis de código** en las páginas de propiedades del proyecto. Esto se puede lograr de una de las siguientes maneras:

   - En **Explorador de soluciones**, seleccione el proyecto. En la barra de menús, seleccione **analizar**  >  **configurar análisis**  >  **de \<projectname> código para **.

   - Haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccione **propiedades**y, a continuación, seleccione la pestaña **análisis de código** .

2. En las listas **configuración** y **plataforma** , seleccione la configuración de compilación y la plataforma de destino.

::: moniker range="vs-2017"

3. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione **Habilitar análisis de código al compilar**. También puede ejecutar el análisis de código manualmente seleccionando **analizar**  >  **Ejecutar**análisis  >  **de código ejecutar análisis \<projectname> de código en **.

::: moniker-end

::: moniker range=">=vs-2019"

3. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione **ejecutar en la compilación** en la sección **analizadores binarios** . También puede ejecutar el análisis de código heredado manualmente. para obtener más información, consulte [Cómo: ejecutar el análisis de código heredado manualmente para código administrado](how-to-run-legacy-code-analysis-manually-for-managed-code.md) .

::: moniker-end

4. Para ver las advertencias del código generado, desactive la casilla **suprimir resultados de código generado** .

    > [!NOTE]
    > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla, y no se sobrescribirá.

::: moniker range="vs-2017"

5. En la lista **ejecutar este conjunto de reglas** , realice una de las acciones siguientes:

::: moniker-end

::: moniker range=">=vs-2019"

5. En la lista **reglas activas** , realice una de las acciones siguientes:

::: moniker-end

   - Seleccione el conjunto de reglas que desea usar.

   - Seleccione esta **\<Browse>** configuración para buscar un conjunto de reglas personalizado existente que no esté en la lista.

   - Defina un [conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Especificar conjuntos de reglas para varios proyectos de una solución

De forma predeterminada, todos los proyectos administrados de una solución tienen asignado el conjunto de reglas de análisis de código *reglas mínimas recomendadas de Microsoft* . Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el cuadro de diálogo **propiedades** de la solución.

1. Abra la solución en Visual Studio.

2. En el menú **analizar** , seleccione **configurar análisis de código para la solución**.

3. Si es necesario, expanda **propiedades comunes**y, a continuación, seleccione **configuración de análisis de código**.

4. Puede especificar un conjunto de reglas para uno o varios proyectos:

    - Para especificar un conjunto de reglas para un proyecto individual, seleccione el nombre del proyecto.

    - Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la **tecla Ctrl** y seleccione los nombres de proyecto.

    - Para especificar todos los proyectos de la solución, mantenga presionada la **tecla Mayús** y haga clic en la lista de proyectos.

5. Seleccione el campo **conjunto de reglas** de un proyecto y, a continuación, seleccione el nombre del conjunto de reglas que desea aplicar.

## <a name="see-also"></a>Consulte también:

- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)
