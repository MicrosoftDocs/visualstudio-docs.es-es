---
title: 'Inicio rápido: Análisis de código para C/C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278480"
---
# <a name="quick-start-code-analysis-for-cc"></a>Inicio rápido: Análisis de código para C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede mejorar la calidad de la aplicación si se analiza con regularidad el código de C o C++. Esto ayuda a descubrir problemas comunes, infracciones de los procedimientos recomendados de programación o defectos que son difíciles de detectar con pruebas. Las advertencias del análisis de código son distintas de los errores y advertencias del compilador, porque el análisis de código busca patrones de código concretos que, aunque son válidos, pueden crear problemas para ti o para otros usuarios del código.  
  
## <a name="in-this-topic"></a>En este tema  
  
- [Configurar conjuntos de reglas para un proyecto](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Ejecutar análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Analizar y resolver las advertencias del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Suprimir las advertencias de análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Crear elementos de trabajo para las advertencias del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Buscar y filtrar resultados del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="configure-rule-sets-for-a-project"></a><a name="BKMK_ConfigureRuleSets"></a> Configurar conjuntos de reglas para un proyecto  
  
1. En **Explorador de soluciones**, abra el menú contextual del nombre del proyecto y, a continuación, elija **propiedades**.  
  
2. Los pasos siguientes son opcionales:  
  
    1. En las listas **configuración** y **plataforma** , elija la configuración de compilación y la plataforma de destino.  
  
    2. De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas. Para ver las advertencias del código generado, desactive la casilla **suprimir resultados de código generado** .  
  
        > [!NOTE]
        > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.  
  
3. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, active la casilla **Habilitar análisis de código para C/C++ al compilar** . También puede ejecutar el análisis de código manualmente si abre el menú **analizar** y, a continuación, elige **Ejecutar Análisis de código en** *projectname*.  
  
4. En la lista **ejecutar este conjunto de reglas** , realice una de las acciones siguientes:  
  
    - Elija el conjunto de reglas que desee usar.  
  
    - Elija esta opción **\<Browse...>** para especificar un conjunto de reglas personalizado existente que no esté en la lista.  
  
    - Defina un conjunto de reglas personalizado.  
  
         Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Conjuntos de reglas estándar de C o C++  
 Visual Studio incluye dos conjuntos de reglas estándar para código nativo:  
  
|Conjunto de reglas|Descripción|  
|--------------|-----------------|  
|Reglas mínimas recomendadas nativas de Microsoft|Este conjunto de reglas se centra en los problemas más graves del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos nativos.|  
|Reglas recomendadas nativas de Microsoft|Este conjunto de reglas cubre una amplia gama de problemas. Incluye todas las reglas de Reglas mínimas recomendadas nativas de Microsoft.|  
  
## <a name="run-code-analysis"></a><a name="BKMK_Run"></a> Ejecutar análisis de código  
 En la página de análisis de código de las páginas de propiedades de proyecto se puede configurar el análisis de código para que se ejecute siempre que se compile el proyecto. También se puede ejecutar el análisis de código de forma manual.  
  
 Para ejecutar el análisis de código en una solución:  
  
- En el menú **Compilar**, elija **Ejecutar análisis de código en la solución**.  
  
  Para ejecutar el análisis de código en proyecto:  
  
- En el Explorador de soluciones, elija el nombre del proyecto.  
  
- En el menú **compilar** , elija **Ejecutar Análisis de código en** *nombre del proyecto*.  
  
  La solución o proyecto se compila y se ejecuta el análisis de código. Los resultados aparecen en la ventana Análisis de código.  
  
## <a name="analyze-and-resolve-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Analizar y resolver advertencias de análisis de código  
 Para analizar una advertencia concreta, elija el título en la ventana Análisis de código. La advertencia se expande para mostrar la información adicional sobre el problema. Cuando es posible, el análisis de código muestra los números de línea y la lógica de análisis que condujeron a la advertencia. Para obtener información detallada sobre la advertencia, incluidas las soluciones posibles al problema, elija el identificador de la advertencia para mostrar el tema de ayuda de la biblioteca de MSDN correspondiente al mensaje.  
  
 Cuando se expande una advertencia, la línea de código que la causó se resalta en el editor de código de Visual Studio.  
  
 Cuando haya entendido el problema, podrá resolverlo en el código. A continuación vuelva a ejecutar el análisis de código para asegurarse de que la advertencia ya no aparece en la ventana de análisis de código y que la corrección no genera nuevas advertencias.  
  
> [!TIP]
> Puedes repetir el análisis de código desde la ventana Análisis de código. Elija el botón **analizar** y elija el ámbito del análisis. Puedes repetir el análisis en toda la solución o en el proyecto seleccionado.  
  
## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Suprimir advertencias de análisis de código  
 A veces, uno decide no corregir una advertencia del análisis de código. Puede ser que para resolverla se necesita un esfuerzo de codificación excesivo en proporción con la probabilidad de que el problema surja en las implementaciones reales del código. O puede que consideres que el análisis que ha dado lugar a la advertencia no es apropiado para ese contexto concreto. Puedes suprimir advertencias individuales de modo que ya no aparezcan en la ventana Análisis de código.  
  
 Para suprimir una advertencia:  
  
1. Si se muestra información detallada, elija el título de la advertencia para expandirla.  
  
2. Elige el vínculo **Acciones** en la parte inferior de la advertencia.  
  
3. Elija **suprimir mensaje** y, a continuación, elija **en origen**.  
  
   Al suprimir un mensaje, se inserta `#pragma warning (disable:` *un identificador warningid* `)` que suprime la advertencia de la línea de código.  
  
## <a name="creating-work-items-for-code-analysis-warnings"></a><a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Crear elementos de trabajo para las advertencias de análisis de código  
 La característica de seguimiento de elemento de trabajo permite registrar errores desde Visual Studio. Para usar esta característica, es necesario conectarse a una instancia de Team Foundation Server.  
  
 **Para crear un elemento de trabajo para una o más advertencias de código de C/C++**  
  
1. En la ventana de análisis de código, expanda y seleccione las advertencias.  
  
2. En el menú contextual de las advertencias, elija **crear elemento de trabajo**y, a continuación, elija el tipo de elemento de trabajo.  
  
3. Visual Studio crea un único elemento de trabajo para las advertencias seleccionadas y muestra el elemento de trabajo en una ventana de documento del IDE.  
  
4. Agregue información adicional y, a continuación, elija **Guardar elemento de trabajo**.  
  
## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Búsqueda y filtrado de resultados de análisis de código  
 Puedes buscar en las listas largas de mensajes de advertencia y filtrar las advertencias en las soluciones de varios proyectos.  
  
1. **Para filtrar las advertencias por título o ID**. de ADVERTENCIA: escriba la palabra clave en el cuadro de texto **filtro** .  
  
2. **Para filtrar las advertencias por proyecto**: en una solución de varios proyectos, elija uno o varios proyectos de la lista en la parte superior derecha de la ventana de análisis de código. Elija el nombre de la solución para mostrar todas las advertencias.  
  
3. **Para filtrar las advertencias por gravedad**: de forma predeterminada, los mensajes de análisis de código tienen asignada una gravedad de **ADVERTENCIA**. Puede asignar la gravedad de uno o más mensajes como **error** en un conjunto de reglas personalizado. Elija **ADVERTENCIA** o **error** para mostrar solo los mensajes a los que se ha asignado la gravedad respectiva. Elija **todos** para mostrar todos los mensajes.
