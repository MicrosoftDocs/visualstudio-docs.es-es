---
title: "Interfaz de usuario del depurador (XSLT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Interfaz de usuario del depurador (XSLT)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describen las ventanas y los cuadros de diálogo del depurador.Solo se explican las partes de la interfaz de usuario que tienen un comportamiento de depuración específico de XSLT.  
  
 Para obtener más información, vea la [Depuración: referencia de la interfaz de usuario](../debugger/debugging-user-interface-reference.md).  
  
## Ventana Locales  
 La ventana Locales muestra información acerca de las variables definidas en la hoja de estilos.Contiene tres columnas de información:  
  
 **Nombre**  
 Esta columna contiene los nombres de todas las variables locales del ámbito actual.Los conjuntos de nodos se controlan como un árbol, por el que puede desplazarse para ver sus subcarpetas.  
  
 **Valor**  
 Esta columna muestra el valor que contiene cada variable.Los nodos de atributo, instrucción de procesamiento, comentario, texto y CData muestran el valor de texto del nodo.Los nodos de espacio de nombres muestran el URI del espacio de nombres.  
  
 **Tipo**  
 Esta columna identifica el tipo de datos de cada variable mostrada en la columna **Nombre**.  
  
 La ventana Locales muestra también las variables de contexto predefinidas que realizan el seguimiento del contexto de la transformación XSLT.En la siguiente tabla se describen las variables de contexto predefinidas que emplea el depurador de XSLT.  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`last()`|El tamaño del contexto.|  
|`position()`|La posición, o número de índice, del nodo de contexto, con respecto al tamaño del contexto.|  
|`self::node()`|El valor del nodo de contexto.|  
  
 Para obtener más información, vea [Cómo: Cambiar el contexto del depurador](../Topic/How%20to:%20Change%20the%20Debugger%20Context.md).  
  
## Ventana de salida  
 La Ventana de salida muestra los mensajes de error o las excepciones de seguridad que se producen durante la depuración.  
  
 El depurador de XSLT utiliza una ventana distinta para mostrar el resultado de la depuración.Se trata de la misma ventana empleada para mostrar el resultado de un comando **Mostrar resultado XSL**.  
  
## Lista de tareas  
 La lista de tareas muestra todos los errores de compilación de la hoja de estilos.Al hacer doble clic en el error, el cursor se desplaza hasta la línea con el error.  
  
 La lista de tareas incluye todos los errores que tienen lugar en los bloques de script del archivo XSLT.  
  
> [!NOTE]
>  El depurador de XSLT no tiene advertencias, así que nunca aparecerán en la lista de tareas.  
  
## Ventana Puntos de interrupción  
 La ventana Puntos de interrupción muestra todos los puntos de interrupción definidos en el proyecto actual.Si se agrega un punto de interrupción mientras la ventana está a la vista, ésta se actualiza automáticamente para mostrar el nuevo punto de interrupción.  
  
 La ventana Puntos de interrupción debe tener el mismo comportamiento que otros depuradores de Visual Studio.  
  
## Ventana Comandos\/Ventana Inmediata  
 No están implementadas en esta versión del depurador de XSLT.  
  
## Ventana Inspección  
 La ventana Inspección se utiliza para evaluar variables.y cambiar sus valores.  
  
 Las variables que se muestran en esta ventana guardan relación con el contexto actual \(el elemento superior de la pila de llamadas\).Si cambia el contexto, la ventana Inspección se actualiza y muestra las variables definidas para ese contexto.  
  
## Ventana Pila de llamadas  
 La ventana Pila de llamadas se utiliza para ver los nombres de las funciones de la pila de llamadas, los tipos de parámetros y los valores de los parámetros.La información de la pila de llamadas solo se muestra cuando el programa que se está depurando se encuentra en estado de interrupción.  
  
 La pila de llamadas representa los diversos contextos por los que atraviesa la ejecución XSLT.Por ejemplo, si hay una llamada de la plantilla "a" a la plantilla "b", la plantilla "a" y la plantilla "b" aparecen en la ventana Pila de llamadas con el contexto actual en primer lugar de la lista.El usuario puede ver la consulta actualmente en ejecución.  
  
 Si las plantillas no tienen un nombre en el archivo XSLT, se utilizan los nombres generados por el procesador XSLT.  
  
 Al hacer clic en otro elemento que no es el que se encuentra en primer lugar de la lista se indica al visor dónde ha tenido lugar la bifurcación de la ejecución XSLT mediante el uso de resaltes y flechas verdes estándar.  
  
## Cuadro de diálogo Inspección rápida  
 El cuadro de diálogo **Inspección rápida** se utiliza para evaluar expresiones XPath 1.0.El nodo de contexto \(el nodo `self::node()` de la ventana Locales\) proporciona el contexto para la ejecución de la expresión XPath.El resultado de la ejecución de la expresión XPath se muestra en la ventana Inspección.  
  
 En la siguiente lista se describen algunas restricciones en la evaluación de expresiones XPath.  
  
-   Solo se permiten funciones XPath integradas.  
  
-   No se permiten funciones XSLT integradas como `document()`, `key()`, etc.  
  
-   No se permiten funciones definidas por el usuario.  
  
 Para obtener más información, vea [Cómo: Evaluar una expresión XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## Ventana Desensamblado  
 La ventana Desensamblado muestra el código ensamblador generado por el compilador de XSLT.Esta ventana se puede utilizar de la misma manera que todas las demás ventanas de desensamblado de Visual Studio.  
  
 Para obtener más información, vea [Cómo: Utilizar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md).  
  
## Vea también  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Ventanas de variables](../Topic/Variable%20Windows.md)