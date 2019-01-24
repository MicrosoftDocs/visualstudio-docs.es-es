---
title: 'Inicio rápido: Análisis de código para C/C ++ | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56f14abab372a6a6e533675b070d420a4dfc7a5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758195"
---
# <a name="quick-start-code-analysis-for-cc"></a>Inicio rápido: Análisis de código para C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede mejorar la calidad de la aplicación si se analiza con regularidad el código de C o C++. Esto ayuda a descubrir problemas comunes, infracciones de los procedimientos recomendados de programación o defectos que son difíciles de detectar con pruebas. Las advertencias de análisis de código difieren de los errores y las advertencias del compilador porque el análisis de código busca patrones de código específicos que, a pesar de ser válidos, podrían crearle problemas a usted o a otras personas que usen el código.  
  
## <a name="in-this-topic"></a>En este tema  
  
-   [Configurar conjuntos de reglas para un proyecto](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Ejecutar análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analizar y resolver las advertencias de análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Suprimir las advertencias de análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Crear elementos de trabajo para el código de las advertencias de análisis](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Buscar y filtrar resultados del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a> Configurar conjuntos de reglas para un proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el nombre del proyecto y, a continuación, elija **propiedades**.  
  
2.  Los pasos siguientes son opcionales:  
  
    1.  En el **configuración** y **plataforma** listas, elija la plataforma de destino y de configuración de compilación.  
  
    2.  De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas. Para ver las advertencias de código generado, desactive la **Suprimir resultados del código generado** casilla de verificación.  
  
        > [!NOTE]
        >  Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.  
  
3.  Para ejecutar análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione el **Habilitar análisis de código para C/C ++ al compilar** casilla de verificación. También puede ejecutar análisis de código si abre el **analizar** menú y, a continuación, elija **ejecutar análisis de código en** *ProjectName*.  
  
4.  En el **ejecutar este conjunto de reglas** lista, realice una de las siguientes acciones:  
  
    -   Elija el conjunto de reglas que desee usar.  
  
    -   Elija  **\<Examinar... >** especificar una regla personalizada existente conjunto que no está en la lista.  
  
    -   Defina un conjunto de reglas personalizado.  
  
         Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Conjuntos de reglas estándar de C o C++  
 Visual Studio incluye dos conjuntos de reglas estándar para código nativo:  
  
|Conjunto de reglas|Descripción|  
|--------------|-----------------|  
|Reglas mínimas recomendadas nativas de Microsoft|Este conjunto de reglas se centra en los problemas más graves del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos nativos.|  
|Reglas recomendadas nativas de Microsoft|Este conjunto de reglas cubre una amplia gama de problemas. Incluye todas las reglas de Reglas mínimas recomendadas nativas de Microsoft.|  
  
##  <a name="BKMK_Run"></a> Ejecutar análisis de código  
 En la página de análisis de código de las páginas de propiedades de proyecto se puede configurar el análisis de código para que se ejecute siempre que se compile el proyecto. También se puede ejecutar el análisis de código de forma manual.  
  
 Para ejecutar el análisis de código en una solución:  
  
- En el menú **Compilar**, elija **Ejecutar análisis de código en la solución**.  
  
  Para ejecutar el análisis de código en proyecto:  
  
- En el Explorador de soluciones, elija el nombre del proyecto.  
  
- En el **compilar** menú, elija **ejecutar análisis de código en** *nombre del proyecto*.  
  
  La solución o proyecto se compila y se ejecuta el análisis de código. Los resultados aparecen en la ventana Análisis de código.  
  
##  <a name="BKMK_Analyze"></a> Analizar y resolver las advertencias de análisis de código  
 Para analizar una advertencia concreta, elija el título en la ventana Análisis de código. La advertencia se expande para mostrar la información adicional sobre el problema. Cuando es posible, el análisis de código muestra los números de línea y la lógica de análisis que condujeron a la advertencia. Para obtener información detallada sobre la advertencia, incluidas las soluciones posibles al problema, elija el identificador de la advertencia para mostrar el tema de ayuda de la biblioteca de MSDN correspondiente al mensaje.  
  
 Cuando se expande una advertencia, la línea de código que la causó se resalta en el editor de código de Visual Studio.  
  
 Una vez comprendido el problema, puede resolverlo en el código. A continuación vuelva a ejecutar el análisis de código para asegurarse de que la advertencia ya no aparece en la ventana de análisis de código y que la corrección no genera nuevas advertencias.  
  
> [!TIP]
>  Puedes repetir el análisis de código desde la ventana Análisis de código. Elija la **analizar** botón y elija el ámbito del análisis. Puedes repetir el análisis en toda la solución o en el proyecto seleccionado.  
  
##  <a name="BKMK_Suppress"></a> Suprimir las advertencias de análisis de código  
 A veces, uno decide no corregir una advertencia del análisis de código. Puede ser que para resolverla se necesita un esfuerzo de codificación excesivo en proporción con la probabilidad de que el problema surja en las implementaciones reales del código. O puede que consideres que el análisis que ha dado lugar a la advertencia no es apropiado para ese contexto concreto. Puedes suprimir advertencias individuales de modo que ya no aparezcan en la ventana Análisis de código.  
  
 Para suprimir una advertencia:  
  
1. Si se muestra información detallada, elija el título de la advertencia para expandirla.  
  
2. Elige el vínculo **Acciones** en la parte inferior de la advertencia.  
  
3. Elija **suprimir mensaje** y, a continuación, elija **en origen**.  
  
   Al suprimir un mensaje se inserta un identificador `#pragma warning (disable:`*WarningId*`)` que suprime la advertencia en la línea de código.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Crear elementos de trabajo para el código de las advertencias de análisis  
 La característica de seguimiento de elemento de trabajo permite registrar errores desde Visual Studio. Para usar esta característica, es necesario conectarse a una instancia de Team Foundation Server.  
  
 **Para crear un elemento de trabajo para una o varias advertencias de código de C o C++**  
  
1.  En la ventana de análisis de código, expanda y seleccione las advertencias.  
  
2.  En el menú contextual para las advertencias, elija **crear elemento de trabajo**y, a continuación, elija el tipo de elemento de trabajo.  
  
3.  Visual Studio crea un único elemento de trabajo para las advertencias seleccionadas y muestra el elemento de trabajo en una ventana de documento del IDE.  
  
4.  Agregar información adicional y, a continuación, elija **Guardar elemento de trabajo**.  
  
##  <a name="BKMK_Search"></a> Buscar y filtrar resultados del análisis de código  
 Puedes buscar en las listas largas de mensajes de advertencia y filtrar las advertencias en las soluciones de varios proyectos.  
  
1.  **Para filtrar las advertencias por título o identificador de advertencia**: escriba la palabra clave en el **filtro** cuadro de texto.  
  
2.  **Para filtrar las advertencias por proyecto**: en una solución multiproyecto, elija uno o varios proyectos en la lista en la parte superior derecha de la ventana de análisis de código. Elija el nombre de la solución para mostrar todas las advertencias.  
  
3.  **Para filtrar las advertencias por gravedad**: de forma predeterminada, los mensajes de análisis de código tienen asignados una gravedad de **advertencia**. Puede asignar la gravedad de uno o más mensajes como **Error** en una regla personalizada establecido. Elija **advertencia** o **Error** para mostrar solo los mensajes que están asignados a la correspondiente gravedad. Elija **todas** para mostrar todos los mensajes.



