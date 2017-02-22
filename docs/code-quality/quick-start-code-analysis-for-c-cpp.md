---
title: "Inicio r&#225;pido: An&#225;lisis de c&#243;digo para C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análisis de código C/C++"
  - "análisis de código, C/C++"
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Inicio r&#225;pido: An&#225;lisis de c&#243;digo para C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se puede mejorar la calidad de la aplicación si se analiza con regularidad el código de C o C\+\+.  Esto ayuda a descubrir problemas comunes, infracciones de los procedimientos recomendados de programación o defectos que son difíciles de detectar con pruebas.  Las advertencias de análisis de código difieren de los errores y las advertencias del compilador porque el análisis de código busca patrones de código específicos que, a pesar de ser válidos, podrían crearle problemas a usted o a otras personas que usen el código.  
  
## En este tema  
  
-   [Configurar conjuntos de reglas para un proyecto](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Ejecutar análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analizar y resolver las advertencias del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Suprimir las advertencias del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Crear elementos de trabajo para las advertencias del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Buscar y filtrar resultados del análisis de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a> Configurar conjuntos de reglas para un proyecto  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nombre del proyecto y, a continuación, elija **Propiedades**.  
  
2.  Los pasos siguientes son opcionales:  
  
    1.  En las listas **Configuración** y **Plataforma**, elija la configuración de compilación y la plataforma de destino.  
  
    2.  De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas.  Para ver las advertencias del código generado, desactive la casilla **Suprimir resultados del código generado**.  
  
        > [!NOTE]
        >  Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas.  Puede ver y mantener el código fuente de un formulario o una plantilla.  
  
3.  Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, active la casilla **Habilitar análisis de código para C\/C\+\+ al compilar**.  También puede ejecutar el análisis de código de forma manual si abre el menú **Analizar** y elige **Ejecutar análisis de código en** *NombreDeProyecto*.  
  
4.  En la lista **Ejecutar este conjunto de reglas**, realice uno de los siguientes procedimientos:  
  
    -   Elija el conjunto de reglas que desee usar.  
  
    -   Elija **\<Examinar...\>** para especificar un conjunto de reglas personalizado existente que no esté en la lista.  
  
    -   Defina un conjunto de reglas personalizado.  
  
         Para obtener más información, vea [Crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### Conjuntos de reglas estándar de C o C\+\+  
 Visual Studio incluye dos conjuntos de reglas estándar para código nativo:  
  
|Conjunto de reglas|Descripción|  
|------------------------|-----------------|  
|Reglas mínimas recomendadas nativas de Microsoft|Este conjunto de reglas se centra en los problemas más graves del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación.  Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos nativos.|  
|Reglas recomendadas nativas de Microsoft|Este conjunto de reglas cubre una amplia gama de problemas.  Incluye todas las reglas de Reglas mínimas recomendadas nativas de Microsoft.|  
  
##  <a name="BKMK_Run"></a> Ejecutar análisis de código  
 En la página de análisis de código de las páginas de propiedades de proyecto se puede configurar el análisis de código para que se ejecute siempre que se compile el proyecto.  También se puede ejecutar el análisis de código de forma manual.  
  
 Para ejecutar el análisis de código en una solución:  
  
-   En el menú **Compilación**, elija **Ejecutar análisis de código en la solución**.  
  
 Para ejecutar el análisis de código en proyecto:  
  
-   En el Explorador de soluciones, elija el nombre del proyecto.  
  
-   En el menú **Compilación**, elija **Ejecutar análisis de código en la solución***Nombre de proyecto*.  
  
 La solución o proyecto se compila y se ejecuta el análisis de código.  Los resultados aparecen en la ventana de análisis de código.  
  
##  <a name="BKMK_Analyze"></a> Analizar y resolver las advertencias del análisis de código  
 Para analizar una advertencia concreta, elija el título de la advertencia en la ventana de análisis de código.  La advertencia se expande para mostrar la información adicional sobre el problema.  Cuando es posible, el análisis de código muestra los números de línea y la lógica de análisis que condujeron a la advertencia.  Para obtener información detallada sobre la advertencia, incluidas las soluciones posibles al problema, elija el identificador de la advertencia para mostrar el tema de ayuda de la biblioteca de MSDN correspondiente al mensaje.  
  
 Cuando se expande una advertencia, la línea de código que la causó se resalta en el editor de código de Visual Studio.  
  
 Una vez comprendido el problema, puede resolverlo en el código.  A continuación vuelva a ejecutar el análisis de código para asegurarse de que la advertencia ya no aparece en la ventana de análisis de código y que la corrección no genera nuevas advertencias.  
  
> [!TIP]
>  Puede volver a ejecutar análisis de código desde la ventana de análisis de código.  Elija el botón **Analizar** y seleccione el ámbito del análisis.  El análisis se puede ejecutar en toda la solución o en un proyecto seleccionado.  
  
##  <a name="BKMK_Suppress"></a> Suprimir las advertencias del análisis de código  
 Puede haber ocasiones en las que no desee corregir una advertencia de análisis de código.  Quizá considere que la resolución de la advertencia requiere demasiada recodificación en comparación con la probabilidad de que el problema surja en cualquier implementación real del código.  También puede pensar que el análisis que se usó en la advertencia no es apropiado para el contexto en cuestión.  En casos así, se pueden suprimir las advertencias individuales para que no vuelva a aparecer en la ventana de análisis de código.  
  
 Para suprimir una advertencia:  
  
1.  Si se muestra información detallada, elija el título de la advertencia para expandirla.  
  
2.  Elija el vínculo **Acciones** en la parte inferior de la advertencia.  
  
3.  Elija **Suprimir mensaje** y, a continuación, elija **En origen**.  
  
 Al suprimir un mensaje se inserta un identificador `#pragma warning (disable:`*WarningId*`)` que suprime la advertencia en la línea de código.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Crear elementos de trabajo para las advertencias del análisis de código  
 La característica de seguimiento de elementos de trabajo permite registrar errores desde Visual Studio.  Para usarla, es necesario conectarse a una instancia de Team Foundation Server.  
  
 **Para crear un elemento de trabajo para una o más advertencias de código de C\/C\+\+**  
  
1.  En la ventana de análisis de código, expanda y seleccione las advertencias.  
  
2.  En el menú contextual de las advertencias, elija **Crear elemento de trabajo** y luego elija el tipo de elemento de trabajo.  
  
3.  Visual Studio crea un único elemento de trabajo para las advertencias seleccionadas y muestra el elemento de trabajo en una ventana de documento del IDE.  
  
4.  Agregue la información adicional que sea necesaria y luego elija **Guardar elemento de trabajo**.  
  
##  <a name="BKMK_Search"></a> Buscar y filtrar resultados del análisis de código  
 Es posible explorar largas listas de mensajes de advertencia y también filtrar advertencias en soluciones multiproyecto.  
  
1.  **Para filtrar las advertencias por título o identificador de advertencia**: escriba la palabra clave en el cuadro de texto **Filtrar**.  
  
2.  **Para filtrar las advertencias por proyecto**: en una solución multiproyecto, elija uno o varios proyectos en la lista de la esquina superior derecha de la ventana de análisis de código.  Elija el nombre de la solución para mostrar todas las advertencias.  
  
3.  **Para filtrar las advertencias por gravedad**: de forma predeterminada, los mensajes de análisis de código tienen asignada una gravedad de **Advertencia**.  Para asignar la gravedad de **Error** a uno o más mensajes, use un conjunto de reglas personalizadas.  Elija **Advertencia** o **Error** para mostrar únicamente los mensajes que tengan asignada la correspondiente gravedad.  Elija **Todo** para mostrar todos los mensajes.