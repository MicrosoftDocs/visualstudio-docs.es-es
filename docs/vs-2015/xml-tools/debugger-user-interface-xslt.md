---
title: Depurador (XSLT) de interfaz de usuario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0117053e47ee9238ee225b9265865b34c6f2140
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300188"
---
# <a name="debugger-user-interface-xslt"></a>Interfaz de usuario del depurador (XSLT)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describen las ventanas y los cuadros de diálogo del depurador. Solo se explican las partes de la interfaz de usuario que tienen un comportamiento de depuración específico de XSLT.  
  
 Para obtener más información, consulte el [referencia de la interfaz de usuario de depuración](../debugger/debugging-user-interface-reference.md).  
  
## <a name="locals-window"></a>Ventana Locales  
 La ventana Locales muestra información acerca de las variables definidas en la hoja de estilos. Contiene tres columnas de información:  
  
 **Name**  
 Esta columna contiene los nombres de todas las variables locales del ámbito actual. Los conjuntos de nodos se controlan como un árbol, por el que puede desplazarse para ver sus subcarpetas.  
  
 **Valor**  
 Esta columna muestra el valor que contiene cada variable. Los nodos de atributo, instrucción de procesamiento, comentario, texto y CData muestran el valor de texto del nodo. Los nodos de espacio de nombres muestran el URI del espacio de nombres.  
  
 **Type**  
 Esta columna identifica el tipo de datos de cada variable mostrada en el **nombre** columna.  
  
 La ventana Locales muestra también las variables de contexto predefinidas que realizan el seguimiento del contexto de la transformación XSLT. En la tabla siguiente se describen las variables de contexto predefinidas que emplea el depurador de XSLT.  
  
|Name|Descripción|  
|----------|-----------------|  
|`last()`|El tamaño del contexto.|  
|`position()`|La posición, o número de índice, del nodo de contexto, con respecto al tamaño del contexto.|  
|`self::node()`|El valor del nodo de contexto.|  
  
 Para obtener más información, consulte [Cómo: cambiar el contexto del depurador](http://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).  
  
## <a name="output-window"></a>Resultados (Ventana)  
 La Ventana de salida muestra los mensajes de error o las excepciones de seguridad que se producen durante la depuración.  
  
 El depurador de XSLT utiliza una ventana distinta para mostrar el resultado de la depuración. Se trata de la misma ventana empleada para mostrar el resultado de una **Mostrar resultado XSL** comando.  
  
## <a name="task-list"></a>Lista de tareas  
 La lista de tareas muestra todos los errores de compilación de la hoja de estilos. Al hacer doble clic en el error, el cursor se desplaza hasta la línea con el error.  
  
 La lista de tareas incluye todos los errores que tienen lugar en los bloques de script del archivo XSLT.  
  
> [!NOTE]
>  El depurador de XSLT no tiene advertencias, así que nunca aparecerán en la lista de tareas.  
  
## <a name="breakpoints-window"></a>Ventana Puntos de interrupción  
 La ventana Puntos de interrupción muestra todos los puntos de interrupción definidos en el proyecto actual. Si se agrega un punto de interrupción mientras la ventana está a la vista, ésta se actualiza automáticamente para mostrar el nuevo punto de interrupción.  
  
 La ventana Puntos de interrupción debe tener el mismo comportamiento que otros depuradores de Visual Studio.  
  
## <a name="command-windowimmediate-window"></a>Ventana Comandos/Ventana Inmediata  
 No están implementadas en esta versión del depurador de XSLT.  
  
## <a name="watch-window"></a>Ventana Inspección  
 La ventana Inspección se utiliza para evaluar variables. y cambiar sus valores.  
  
 Las variables que se muestran en esta ventana guardan relación con el contexto actual (el elemento superior de la pila de llamadas). Si cambia el contexto, la ventana Inspección se actualiza y muestra las variables definidas para ese contexto.  
  
## <a name="call-stack-window"></a>Ventana Pila de llamadas  
 La ventana Pila de llamadas se utiliza para ver los nombres de las funciones de la pila de llamadas, los tipos de parámetros y los valores de los parámetros. La información de la pila de llamadas solo se muestra cuando el programa que se está depurando se encuentra en estado de interrupción.  
  
 La pila de llamadas representa los diversos contextos por los que atraviesa la ejecución XSLT. Por ejemplo, si hay una llamada de la plantilla "a" a la plantilla "b", la plantilla "a" y la plantilla "b" aparecen en la ventana Pila de llamadas con el contexto actual en primer lugar de la lista. El usuario puede ver la consulta actualmente en ejecución.  
  
 Si las plantillas no tienen un nombre en el archivo XSLT, se utilizan los nombres generados por el procesador XSLT.  
  
 Al hacer clic en otro elemento que no es el que se encuentra en primer lugar de la lista se indica al visor dónde ha tenido lugar la bifurcación de la ejecución XSLT mediante el uso de resaltes y flechas verdes estándar.  
  
## <a name="quickwatch-dialog-box"></a>Cuadro de diálogo Inspección rápida  
 El **Inspección rápida** cuadro de diálogo se usa para evaluar expresiones XPath 1.0. El nodo de contexto (el nodo `self::node()` de la ventana Locales) proporciona el contexto para la ejecución de la expresión XPath. El resultado de la ejecución de la expresión XPath se muestra en la ventana Inspección.  
  
 En la siguiente lista se describen algunas restricciones en la evaluación de expresiones XPath.  
  
-   Solo se permiten funciones XPath integradas.  
  
-   No se permiten funciones XSLT integradas como `document()`, `key()`, etc.  
  
-   No se permiten funciones definidas por el usuario.  
  
 Para obtener más información, consulte [Cómo: evaluar una expresión XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>Ventana Desensamblado  
 La ventana Desensamblado muestra el código ensamblador generado por el compilador de XSLT. Esta ventana se puede utilizar de la misma manera que todas las demás ventanas de desensamblado de Visual Studio.  
  
 Para obtener más información, [Cómo: usar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Windows variable](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)

