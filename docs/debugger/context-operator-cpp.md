---
title: "Operador de contexto (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.operators"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "expresiones [C++], depurador nativo"
  - "evaluación"
  - "especificadores de formato, expresiones"
  - "operador de contexto, en expresiones"
  - "depuración [C++], expresiones"
  - "evaluador de expresiones nativas"
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Operador de contexto (C++)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar el operador de contexto en C\+\+ para calificar una ubicación de punto de interrupción, un nombre de variable o una expresión. El operador de contexto resulta útil para especificar un nombre desde un ámbito externo que se encuentra oculto por un nombre local.  
  
##  <a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sintaxis  
 Hay dos formas de especificar el contexto:  
  
1.  {,,\[*módulo*\] } *expresión*  
  
     Las llaves deben contener dos comas y el nombre o la ruta de acceso completa del módulo \(archivo ejecutable o DLL\).  
  
     Por ejemplo, para establecer un punto de interrupción en la función de `SomeFunction` de EXAMPLE.dll:  
  
    ```cpp  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2.  *module*\!*expresión*  
  
    ```cpp  
    EXAMPLE.dll!SomeFunction  
    ```  
  
-   *module* es el nombre de un módulo. Puede utilizar una ruta de acceso completa para eliminar la ambigüedad entre módulos con el mismo nombre.  
  
     Si la ruta de acceso del *módulo* incluye una coma, un espacio incrustado o una llave, debe encerrar el nombre de la ruta de acceso entre comillas para que el analizador de contexto pueda reconocer correctamente la cadena. Las comillas simples se consideran parte de un nombre de archivo de Windows, por lo que deben utilizarse comillas dobles. Por ejemplo,  
  
    ```  
    {,"a long, long, library name.dll", } g_Var  
    ```  
  
-   *expression* es cualquier expresión de C\+\+ válida que se resuelve en un destino válido, por ejemplo un nombre de función, nombre de variable o dirección del puntero del *módulo*.  
  
 Cuando el evaluador de expresiones encuentra un símbolo en una expresión, busca el símbolo en el siguiente orden:  
  
1.  Salida del ámbito léxico, empezando por el bloque actual, la serie de instrucciones entre llaves y continuando la salida con el bloque de inclusión. El bloque actual es el código que contiene la ubicación actual, la dirección del puntero de instrucción.  
  
2.  Ámbito de función. La función actual.  
  
3.  Ámbito de clase, si la ubicación actual está dentro de una función miembro de C\+\+. El ámbito de clase incluye todas las clases base. El evaluador de expresiones utiliza las reglas de dominación normales.  
  
4.  Símbolos globales del módulo actual.  
  
5.  Símbolos públicos del programa actual.