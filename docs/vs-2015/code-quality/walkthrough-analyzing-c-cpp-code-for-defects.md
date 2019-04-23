---
title: 'Tutorial: Análisis de código de C/C ++ en previsión de defectos | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: dcd862b6ff9c94b8de3fc8b5a56164549fefe8ca
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099512"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Tutorial: Analizar código de C/C++ en busca de defectos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial muestra cómo analizar el código de C/C ++ en previsión de defectos de código posible mediante el uso de la herramienta de análisis de código para código de C o C++.  
  
 En este tutorial, paso a través del proceso de uso de análisis de código para analizar el código de C/C ++ en previsión de defectos de código posibles.  
  
 Completar los pasos siguientes:  
  
- Ejecutar análisis de código en código nativo.  
  
- Analizar las advertencias de defectos de código.  
  
- Tratar advertencia como un error.  
  
- Anotar el código fuente para mejorar el análisis de defectos de código.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
- Una copia de la [ejemplo de demostración](../code-quality/demo-sample.md).  
  
- Conocimientos básicos de C o C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Para ejecutar el análisis de defectos de código en código nativo  
  
1. Abra la solución de demostración en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     La solución de demostración se rellena ahora **el Explorador de soluciones**.  
  
2. En el menú **Compilar**, haga clic en **Recompilar solución**.  
  
     La solución se compila sin errores ni advertencias.  
  
3. En **el Explorador de soluciones**, seleccione el proyecto CodeDefects.  
  
4. En el menú **Proyecto**, haga clic en **Propiedades**.  
  
     El **páginas de propiedades de CodeDefects** se muestra el cuadro de diálogo.  
  
5. Haga clic en **análisis de código**.  
  
6. Haga clic en el **Habilitar análisis de código para C/C ++ al compilar** casilla de verificación.  
  
7. Recompile el proyecto CodeDefects.  
  
     Advertencias de análisis de código se muestran en el **lista de errores**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Para analizar las advertencias de defectos de código  
  
1. En el **vista** menú, haga clic en **lista de errores**.  
  
     Según el perfil de desarrollador que eligió en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], podría tener para que apunte a **Other Windows** en el **vista** menú y, a continuación, haga clic en **lista de errores**.  
  
2. En el **lista de errores**, haga doble clic en la siguiente advertencia:  
  
     warning C6230: Conversión implícita entre tipos semánticamente diferentes: usando HRESULT en un contexto booleano.  
  
     El editor de código muestra la línea que produjo la advertencia en la función `bool``ProcessDomain()`. Esta advertencia indica que se está utilizando un valor de HRESULT en una instrucción 'if' donde se espera un resultado booleano.  
  
3. Corregir esta advertencia mediante la macro SUCCEEDED. El código debe ser similar el código siguiente:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. En el **lista de errores**, haga doble clic en la siguiente advertencia:  
  
     warning C6282: Operador incorrecto: asignación de constante en el contexto de la prueba. ¿Pretendía indicar ==?  
  
5. Corregir esta advertencia mediante la comprobación de igualdad. El código debe ser similar al código siguiente:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Tratar advertencia como un error  
  
1. En el archivo Bug.cpp, agregue la siguiente `#pragma` instrucción al principio del archivo para tratar la advertencia C6001 como un error:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. Recompile el proyecto CodeDefects.  
  
     En el **lista de errores**, C6001 aparecerá ahora como un error.  
  
3. Corrija los errores de C6001 dos restantes en el **lista de errores** inicializando `i` y `j` en 0.  
  
4. Recompile el proyecto CodeDefects.  
  
     El proyecto se compila sin errores ni advertencias.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Para corregir las advertencias de anotación de código fuente en annotation.c  
  
1. En el Explorador de soluciones, seleccione el proyecto de anotaciones.  
  
2. En el menú **Proyecto**, haga clic en **Propiedades**.  
  
     El **páginas de propiedades de las anotaciones** se muestra el cuadro de diálogo.  
  
3. Haga clic en **análisis de código**.  
  
4. Seleccione el **Habilitar análisis de código para C/C ++ al compilar** casilla de verificación.  
  
5. Recompile el proyecto de anotaciones.  
  
6. En el **lista de errores**, haga doble clic en la siguiente advertencia:  
  
     Advertencia C6011: Desreferenciación del puntero NULL 'newNode'.  
  
     Esta advertencia indica un error por el llamador para comprobar el valor devuelto. En este caso, una llamada a **AllocateNode** podría devolver un valor NULL (vea el archivo de encabezado annotations.h declaración de función correspondiente AllocateNode).  
  
7. Abra el archivo annotations.cpp.  
  
8. Para corregir esta advertencia, utilice una instrucción 'if' para probar el valor devuelto. El código debe ser similar el código siguiente:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Recompile el proyecto de anotaciones.  
  
     El proyecto se compila sin errores ni advertencias.  
  
### <a name="to-use-source-code-annotation"></a>Para usar la anotación del código fuente  
  
1. Anotar parámetros formales y devolver el valor de la función `AddTail` mediante el uso de las condiciones anteriores y posteriores tal como se muestra en este ejemplo:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. Recompile el proyecto de anotaciones.  
  
3. En el **lista de errores**, haga doble clic en la siguiente advertencia:  
  
     Advertencia C6011: Desreferenciación del puntero NULL 'node'.  
  
     Esta advertencia indica que el nodo pasado a la función podría ser null e indica el número de línea donde se produjo la advertencia.  
  
4. Para corregir esta advertencia, utilice una instrucción 'if' para probar el valor devuelto. El código debe ser similar el código siguiente:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5. Recompile el proyecto de anotaciones.  
  
     El proyecto se compila sin errores ni advertencias.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Análisis de código administrado en previsión de defectos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
