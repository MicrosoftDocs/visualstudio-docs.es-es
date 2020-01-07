---
title: Configurar análisis de código
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
ms.openlocfilehash: fe144e8de67264c9d89f6a240ef815afac9a4655
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587568"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Cómo: configurar el análisis heredado para código administrado

En Visual Studio, puede elegir en una lista de [conjuntos de reglas](../code-quality/rule-set-reference.md) de análisis de código para aplicarlos a un proyecto de código administrado. De forma predeterminada, el **reglas mínimas recomendadas de Microsoft** se selecciona el conjunto de reglas, pero puede aplicar una regla diferente establecer si lo desea. Conjuntos de reglas pueden aplicarse a uno o varios proyectos en una solución.

> [!NOTE]
> Este artículo se aplica al análisis heredado y no a los [analizadores de código basados en .net Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurar un conjunto de reglas para un proyecto de .NET Framework

1. Abra el **análisis de código** ficha en páginas de propiedades del proyecto. Esto se puede lograr de una de las siguientes maneras:

   - En **el Explorador de soluciones**, seleccione el proyecto. En la barra de menús, seleccione **analizar** > **configurar análisis de código** > **para \<NombreDelProyecto >** .

   - Haga clic en el proyecto en **el Explorador de soluciones** y seleccione **propiedades**y, a continuación, seleccione el **análisis de código** ficha.

2. En el **configuración** y **plataforma** listas, seleccione la plataforma de destino y de configuración de compilación.

::: moniker range="vs-2017"

3. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione **Habilitar análisis de código al compilar**. También puede ejecutar análisis de código seleccionando **analizar** > **ejecutar análisis de código** > **ejecutar análisis de código en \<NombreDelProyecto >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione **ejecutar en la compilación** en la sección **analizadores binarios** . También puede ejecutar análisis de código seleccionando **analizar** > **ejecutar análisis de código** > **ejecutar análisis de código en \<NombreDelProyecto >** .

::: moniker-end

4. Para ver las advertencias de código generado, desactive la **Suprimir resultados del código generado** casilla de verificación.

    > [!NOTE]
    > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla, y no se sobrescribirá.

::: moniker range="vs-2017"

5. En el **ejecutar este conjunto de reglas** lista, realice una de las siguientes acciones:

::: moniker-end

::: moniker range=">=vs-2019"

5. En la lista **reglas activas** , realice una de las acciones siguientes:

::: moniker-end

   - Seleccione el conjunto de reglas que desea usar.

   - Seleccione **\<examinar >** para buscar un conjunto de reglas personalizado existente que no esté en la lista.

   - Definir un [conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Especificar conjuntos de reglas para varios proyectos en una solución

De forma predeterminada, todos los proyectos administrados de una solución se asignan los *reglas mínimas recomendadas de Microsoft* conjunto de reglas de análisis de código. Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el **propiedades** cuadro de diálogo de la solución.

1. Abra la solución en Visual Studio.

2. En el **analizar** menú, seleccione **configurar análisis de código para solución**.

3. Si es necesario, expanda **propiedades comunes**y, a continuación, seleccione **configuración de análisis de código**.

4. Puede especificar un conjunto de reglas para uno o varios proyectos:

    - Para especificar un conjunto de reglas para un proyecto individual, seleccione el nombre del proyecto.

    - Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la tecla **Ctrl** y seleccione los nombres de proyecto.

    - Para especificar todos los proyectos de la solución, mantenga presionada la tecla **MAYÚS** y haga clic en la lista de proyectos.

5. Seleccione el **Pravidel** campo de un proyecto y, a continuación, seleccione el nombre de la regla establece que desea aplicar.

## <a name="see-also"></a>Vea también

- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)
