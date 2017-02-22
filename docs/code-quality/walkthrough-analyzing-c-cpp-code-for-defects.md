---
title: "Tutorial: Analizar c&#243;digo de C/C++ en previsi&#243;n de defectos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "C/C++, análisis de código"
  - "herramienta de análisis de código, tutoriales"
  - "análisis de código, tutoriales"
  - "código, analizar C/C++"
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Analizar c&#243;digo de C/C++ en previsi&#243;n de defectos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo analizar el código C\/C\+\+ para comprobar si tiene defectos de código potenciales utilizando la herramienta de análisis de código para el código C\/C\+\+.  
  
 En este tutorial, se describe paso a paso el proceso de utilizar el análisis de código para analizar el código de C\/C\+\+ en previsión de posibles defectos de código.  
  
 Llevará a cabo los pasos siguientes:  
  
-   Ejecutar el análisis de código en el código nativo.  
  
-   Analizar las advertencias de defectos de código.  
  
-   Tratar las advertencias como errores.  
  
-   Anotar el código fuente para mejorar el análisis de defectos de código.  
  
## Requisitos previos  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  
  
-   Una copia de [Ejemplo de demostración](../code-quality/demo-sample.md).  
  
-   Conocimientos básicos de C\/C\+\+.  
  
### Para ejecutar el análisis de defectos de código en código nativo  
  
1.  Abra la solución Demo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     La solución Demo rellenará el **Explorador de soluciones**.  
  
2.  En el menú **Compilar**, haga clic en **Recompilar solución**.  
  
     La solución se compilará sin errores ni advertencias.  
  
3.  En el **Explorador de soluciones**, seleccione el proyecto CodeDefects.  
  
4.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
     Aparece el cuadro de diálogo **Páginas de propiedades de CodeDefects**.  
  
5.  Haga clic en **Análisis de código**.  
  
6.  Haga clic en la casilla **Habilitar análisis de código para C\/C\+\+ al compilar**.  
  
7.  Recompile el proyecto CodeDefects.  
  
     Se mostrarán advertencias de análisis de código en la **Lista de errores**.  
  
### Para analizar las advertencias de defectos de código  
  
1.  En el menú **Ver**, haga clic en **Lista de errores**.  
  
     Dependiendo del perfil del programador seleccionado en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quizá deba elegir el comando **Otras ventanas** del menú **Ver** y, a continuación, hacer clic en **Lista de errores**.  
  
2.  En la **Lista de errores**, haga doble clic en la siguiente advertencia:  
  
     Advertencia C6230: Conversión de tipos implícita entre tipos semánticamente diferentes: uso de HRESULT en un contexto booleano.  
  
     El editor de código muestra la línea que produjo la advertencia en la función `bool` `ProcessDomain()`.  Esta advertencia indica que se está utilizando un valor HRESULT en una instrucción 'if' cuando se espera un resultado booleano.  
  
3.  Corrija esta advertencia utilizando la macro SUCCEEDED.  El código debería ser similar al ejemplo siguiente.  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  En la **Lista de errores**, haga doble clic en la siguiente advertencia:  
  
     Advertencia C6282: Operador incorrecto: asignación a constante en contexto de pruebas.  ¿Pretendía indicar \=\=?  
  
5.  Corrija esta advertencia probando la igualdad.  El código debe ser similar al siguiente:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### Para tratar las advertencias como errores  
  
1.  En el archivo Bug.cpp, agregue la siguiente instrucción `#pragma` al principio del archivo para tratar la advertencia C6001 como un error:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Recompile el proyecto CodeDefects.  
  
     En la **Lista de errores**, C6001 aparecerá ahora como un error.  
  
3.  Corrija los dos errores de C6001 restantes en la **Lista de errores** inicializando `i` y `j` en 0.  
  
4.  Recompile el proyecto CodeDefects.  
  
     El proyecto se compilará sin advertencias ni errores.  
  
### Para corregir las advertencias de anotación de código fuente en annotation.c  
  
1.  En el Explorador de soluciones, seleccione el proyecto Annotations.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
     Aparece el cuadro de diálogo **Páginas de propiedades de anotaciones**.  
  
3.  Haga clic en **Análisis de código**.  
  
4.  Seleccione la casilla **Habilitar análisis de código para C\/C\+\+ al compilar**.  
  
5.  Recompile el proyecto Annotations.  
  
6.  En la **Lista de errores**, haga doble clic en la siguiente advertencia:  
  
     Advertencia C6011: Desreferenciación del puntero NULL 'newNode'.  
  
     Esta advertencia indica que el llamador no ha conseguido comprobar el valor devuelto.  En este caso, una llamada a **AllocateNode** puede devolver un valor NULL \(vea en el archivo de encabezado annotations.h la declaración de función correspondiente a AllocateNode\).  
  
7.  Abra el archivo annotations.cpp.  
  
8.  Para corregir esta advertencia, utilice una instrucción 'if' para probar el valor devuelto.  El código debería ser similar al ejemplo siguiente.  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Recompile el proyecto Annotations.  
  
     El proyecto se compilará sin advertencias ni errores.  
  
### Para utilizar la anotación del código fuente  
  
1.  Anote los parámetros formales y el valor devuelto de la función `AddTail` utilizando las condiciones Pre y Post como se muestra en este ejemplo:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Recompile el proyecto Annotations.  
  
3.  En la **Lista de errores**, haga doble clic en la siguiente advertencia:  
  
     Advertencia C6011: Desreferenciación del puntero NULL 'node'.  
  
     Esta advertencia indica que el nodo pasado en la función podría ser nulo, e indica el número de línea donde se provocó la advertencia.  
  
4.  Para corregir esta advertencia, utilice una instrucción 'if' para probar el valor devuelto.  El código debería ser similar al ejemplo siguiente.  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Recompile el proyecto Annotations.  
  
     El proyecto se compilará sin advertencias ni errores.  
  
## Vea también  
 [Tutorial: Analizar código administrado en previsión de defectos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)