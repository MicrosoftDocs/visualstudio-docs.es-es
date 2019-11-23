---
title: 'Tutorial: Analizar código de C/C++ en previsión de defectos'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: bdb99cf487995859b9623f11b3559f1b5e7e3ca7
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018344"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Tutorial: Analizar código de C/C++ en previsión de defectos

En este tutorial se muestra cómo analizar CC++ /code para detectar posibles defectos de código mediante la herramienta de análisis deC++ código para C/Code.

- Ejecutar análisis de código en código nativo.
- Analizar advertencias de defectos de código.
- Tratar ADVERTENCIA como un error.
- Anote el código fuente para mejorar el análisis del defecto de código.

## <a name="prerequisites"></a>Requisitos previos

- Una copia del [ejemplo demo](../code-quality/demo-sample.md).
- Conocimientos básicos de C/C++.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Para ejecutar el análisis de defectos de código en código nativo

1. Abra la solución demo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     La solución demo ahora rellena **Explorador de soluciones**.

2. En el menú **Compilar**, haga clic en **Recompilar solución**.

     La solución se compila sin errores ni advertencias.

3. En **Explorador de soluciones**, seleccione el proyecto CodeDefects.

4. En el menú **Proyecto**, haga clic en **Propiedades**.

     Se muestra el cuadro de diálogo **páginas de propiedades de CodeDefects** .

5. Haga clic en **análisis de código**.

6. Active la casilla **Habilitar análisis de código paraC++ C/al compilar** .

7. Vuelva a generar el proyecto CodeDefects.

     Las advertencias de análisis de código se muestran en el **lista de errores**.

### <a name="to-analyze-code-defect-warnings"></a>Para analizar las advertencias de defectos de código

1. En el menú **Ver** , haga clic en **lista de errores**.

     Según el perfil de desarrollador elegido en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], es posible que tenga que señalar a **otras ventanas** en el menú **Ver** y, a continuación, hacer clic en **lista de errores**.

2. En el **lista de errores**, haga doble clic en la siguiente ADVERTENCIA:

     ADVERTENCIA C6230: conversión implícita entre tipos semánticamente diferentes: usando HRESULT en un contexto booleano.

     El editor de código muestra la línea que causó la advertencia en la función `bool ProcessDomain()`. Esta advertencia indica que se está usando un HRESULT en una instrucción ' if ' en la que se espera un resultado booleano.

3. Corrija esta advertencia mediante la macro SUCCEEDED. El código debe ser similar al código siguiente:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. En el **lista de errores**, haga doble clic en la siguiente ADVERTENCIA:

     ADVERTENCIA C6282: operador incorrecto: asignación a la constante en el contexto de prueba. Was = = ¿está previsto?

5. Corrija esta advertencia comprobando si son iguales. El código debe ser similar al código siguiente:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Para tratar la advertencia como un error

1. En el archivo bug. cpp, agregue la siguiente instrucción `#pragma` al principio del archivo para tratar la advertencia C6001 como un error:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Vuelva a generar el proyecto CodeDefects.

     En el **lista de errores**, C6001 aparece ahora como un error.

3. Corrija los dos errores C6001 restantes en el **lista de errores** inicializando `i` y `j` en 0.

4. Vuelva a generar el proyecto CodeDefects.

     El proyecto se compila sin advertencias ni errores.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Para corregir las advertencias de anotación de código fuente en Annotation. c

1. En Explorador de soluciones, seleccione el proyecto Annotations.

2. En el menú **Proyecto**, haga clic en **Propiedades**.

     Se muestra el cuadro de diálogo **páginas de propiedades de anotaciones** .

3. Haga clic en **análisis de código**.

4. Active la casilla **Habilitar análisis de código paraC++ C/al compilar** .

5. Vuelva a generar el proyecto Annotations.

6. En el **lista de errores**, haga doble clic en la siguiente ADVERTENCIA:

     ADVERTENCIA C6011: desreferenciando el puntero nulo ' newNode '.

     Esta advertencia indica que el llamador no pudo comprobar el valor devuelto. En este caso, una llamada a **AllocateNode** puede devolver un valor null (vea el archivo de encabezado Annotations. h para la declaración de función para AllocateNode).

7. Abra el archivo Annotations. cpp.

8. Para corregir esta advertencia, utilice una instrucción ' if ' para probar el valor devuelto. El código debe ser similar al código siguiente:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Vuelva a generar el proyecto Annotations.

     El proyecto se compila sin advertencias ni errores.

### <a name="to-use-source-code-annotation"></a>Para utilizar la anotación del código fuente

1. Anote los parámetros formales y el valor devuelto de la función `AddTail` mediante las condiciones pre y post, tal como se muestra en este ejemplo:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Recompilar proyecto de anotaciones.

3. En el **lista de errores**, haga doble clic en la siguiente ADVERTENCIA:

     ADVERTENCIA C6011: desreferenciando el puntero NULL ' node '.

     Esta advertencia indica que el nodo pasado a la función puede ser null e indica el número de línea donde se produjo la advertencia.

4. Para corregir esta advertencia, utilice una instrucción ' if ' para probar el valor devuelto. El código debe ser similar al código siguiente:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Recompilar proyecto de anotaciones.

     El proyecto se compila sin advertencias ni errores.

## <a name="see-also"></a>Vea también

[Tutorial: analizar código administrado para defectos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[análisis de código paraC++ C/](../code-quality/code-analysis-for-c-cpp-overview.md)
