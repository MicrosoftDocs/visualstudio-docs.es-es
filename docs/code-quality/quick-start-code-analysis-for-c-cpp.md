---
title: 'Inicio rápido: Análisis de código para C/C++'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 3aefc42e77c6ccaf14a426a26e12b81b49bb5632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818775"
---
# <a name="quickstart-code-analysis-for-cc"></a>Inicio rápido: Análisis de código para C/C++

Se puede mejorar la calidad de la aplicación si se analiza con regularidad el código de C o C++. Esto ayuda a descubrir problemas comunes, infracciones de los procedimientos recomendados de programación o defectos que son difíciles de detectar con pruebas. Las advertencias del análisis de código son distintas de los errores y advertencias del compilador, porque el análisis de código busca patrones de código concretos que, aunque son válidos, pueden crear problemas para ti o para otros usuarios del código.

## <a name="configure-rule-sets-for-a-project"></a>Configurar conjuntos de reglas para un proyecto

1. En **el Explorador de soluciones**, abra el menú contextual para el nombre del proyecto y, a continuación, elija **propiedades**.

2. Los pasos siguientes son opcionales:

    1. En el **configuración** y **plataforma** listas, elija la plataforma de destino y de configuración de compilación.

    2. De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas. Para ver las advertencias de código generado, desactive la **Suprimir resultados del código generado** casilla de verificación.

        > [!NOTE]
        > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.

3. Para ejecutar análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione el **Habilitar análisis de código para C/C ++ al compilar** casilla de verificación. También puede ejecutar análisis de código si abre el **analizar** menú y, a continuación, elija **ejecutar análisis de código en** *ProjectName*.

4. En el **ejecutar este conjunto de reglas** lista, realice una de las siguientes acciones:

    - Elija el conjunto de reglas que desee usar.

    - Elija  **\<Examinar... >** especificar una regla personalizada existente conjunto que no está en la lista.

    - Definir un [conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Conjuntos de reglas estándar de C o C++

Visual Studio incluye dos conjuntos de reglas estándar para código nativo:

|Conjunto de reglas|Descripción|
|--------------|-----------------|
|Reglas mínimas recomendadas nativas de Microsoft|Este conjunto de reglas se centra en los problemas más graves del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos nativos.|
|Reglas recomendadas nativas de Microsoft|Este conjunto de reglas cubre una amplia gama de problemas. Incluye todas las reglas de Reglas mínimas recomendadas nativas de Microsoft.|

## <a name="run-code-analysis"></a>Ejecutar análisis de código

En la página de análisis de código de las páginas de propiedades de proyecto se puede configurar el análisis de código para que se ejecute siempre que se compile el proyecto. También se puede ejecutar el análisis de código de forma manual.

Para ejecutar el análisis de código en una solución:

- En el menú **Compilar**, elija **Ejecutar análisis de código en la solución**.

Para ejecutar el análisis de código en proyecto:

1. En el Explorador de soluciones, elija el nombre del proyecto.

2. En el **compilar** menú, elija **ejecutar análisis de código en** *nombre del proyecto*.

   La solución o proyecto se compila y se ejecuta el análisis de código. Los resultados aparecen en la lista de errores.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizar y resolver las advertencias del análisis de código

Para analizar una advertencia concreta, elija el título de la advertencia en la lista de errores. La advertencia se expande para mostrar la información adicional sobre el problema. Cuando es posible, el análisis de código muestra los números de línea y la lógica de análisis que condujeron a la advertencia. Para obtener información detallada sobre la advertencia, incluidas las soluciones posibles para el problema, elija el identificador de advertencia para mostrar el tema de ayuda en línea correspondiente.

Cuando se selecciona una advertencia, se resalta la línea de código que produjo la advertencia en el editor de código de Visual Studio.

Cuando haya entendido el problema, podrá resolverlo en el código. A continuación, vuelva a ejecutar el análisis de código para asegurarse de que ya no aparece la advertencia en la lista de errores y que la corrección no genera nuevas advertencias.

## <a name="suppress-code-analysis-warnings"></a>Suprimir advertencias de análisis de código

A veces, uno decide no corregir una advertencia del análisis de código. Puede ser que para resolverla se necesita un esfuerzo de codificación excesivo en proporción con la probabilidad de que el problema surja en las implementaciones reales del código. O puede que consideres que el análisis que ha dado lugar a la advertencia no es apropiado para ese contexto concreto. Puede suprimir advertencias individuales de modo que ya no aparezcan en la lista de errores.

Para suprimir una advertencia:

1. Si se muestra información detallada, elija el título de la advertencia para expandirla.

2. Elige el vínculo **Acciones** en la parte inferior de la advertencia.

3. Elija **suprimir mensaje** y, a continuación, elija **en origen**.

   Al suprimir un mensaje se inserta `#pragma warning (disable:[warning ID])` que suprime la advertencia en la línea de código.

## <a name="create-work-items-for-code-analysis-warnings"></a>Crear elementos de trabajo para el código de las advertencias de análisis

La característica de seguimiento de elemento de trabajo permite registrar errores desde Visual Studio. Para usar esta característica, es necesario conectarse a una instancia de Team Foundation Server.

**Para crear un elemento de trabajo para una o varias advertencias de código de C o C++**

1. En la lista de errores, expanda y seleccione las advertencias.

2. En el menú contextual para las advertencias, elija **crear elemento de trabajo**y, a continuación, elija el tipo de elemento de trabajo.

3. Visual Studio crea un único elemento de trabajo para las advertencias seleccionadas y muestra el elemento de trabajo en una ventana de documento del IDE.

4. Agregar información adicional y, a continuación, elija **Guardar elemento de trabajo**.

## <a name="search-and-filter-code-analysis-results"></a>Buscar y filtrar resultados del análisis de código

Puedes buscar en las listas largas de mensajes de advertencia y filtrar las advertencias en las soluciones de varios proyectos.

- **Para filtrar las advertencias por título o identificador de advertencia**: escriba la palabra clave en el cuadro de búsqueda.

- **Para filtrar las advertencias por gravedad**: de forma predeterminada, los mensajes de análisis de código tienen asignados una gravedad de **advertencia**. Puede asignar la gravedad de uno o más mensajes como **Error** en una regla personalizada establecido. En el **gravedad** columna de la **lista de errores**, elija la flecha desplegable y, a continuación, en el icono de filtro. Elija **advertencia** o **Error** para mostrar solo los mensajes que están asignados a la correspondiente gravedad. Elija **seleccionar todo** para mostrar todos los mensajes.

## <a name="see-also"></a>Vea también

[Análisis de código para C/C ++](../code-quality/code-analysis-for-c-cpp-overview.md)