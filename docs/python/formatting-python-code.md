---
title: Formato de código de Python
description: Describe cómo volver a formatear código de Python automáticamente en Visual Studio que incluya comentarios, instrucciones, ajuste y espaciado.
ms.date: 10/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: b0ce6b5db57b4f6140fb164391ebf5c07e623baf
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219554"
---
# <a name="format-python-code"></a>Aplicar formato a código de Python

Visual Studio permite volver a aplicar formato rápidamente al código para que coincida con las opciones de formato configuradas previamente.

- Para aplicar formato a una selección: seleccione **Editar** > **Opciones avanzadas** > **Dar formato a la selección** o presione **Ctrl**+**E** > **F**.
- Para aplicar formato a todo el archivo: seleccione **Editar** > **Opciones avanzadas** > **Dar formato al documento** o presione **Ctrl**+**E** > **D**.

Las opciones se configuran en **Herramientas** > **Opciones** > **Editor de texto** > **Python** > **Formato** y sus pestañas anidadas. Es necesario seleccionar **Mostrar todas las configuraciones** para que aparezcan estas opciones:

![Opciones de formato de Python en Visual Studio](media/options-editor-formatting.png)

Las opciones de formato se establecen de forma predeterminada para que coincidan con un supraconjunto de la [guía de estilo PEP 8](http://www.python.org/dev/peps/pep-0008/). La pestaña **General** determina cuándo se aplica el formato; la configuración de las otras tres pestañas se describe en este artículo.

La [compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md) también agrega el práctico comando [**Rellenar párrafo del comentario**](#fill-comment-paragraph-command) al menú **Editar** > **Opciones avanzadas**, como se describe en una sección posterior.

## <a name="spacing"></a>Espaciado

El **espaciado** controla dónde se insertan o quitan los espacios en torno a diversas construcciones de lenguajes. Cada opción tiene tres valores posibles:

- Activada: garantiza que se aplica el espaciado.
- Desactivada: elimina el espaciado.
- Indeterminada: deja el formato original en su sitio.

En las tablas siguientes se proporcionan ejemplos de las distintas opciones:

| Opción Definiciones de clase | Activado | Borrado |
| --- | --- | --- | 
| **Insertar espacio entre el nombre de la declaración de clase y la lista de bases** | `class X (object): pass` | `class X(object): pass` | 
| **Insertar espacio en paréntesis de lista de bases** | `class X( object ): pass` | `class X(object): pass` |
| **Insertar espacio en paréntesis de lista de bases vacía** | `class X( ): pass` | `class X(): pass` |

<br/>

| Opción Definiciones de función | Activado | Borrado |
| --- | --- | --- |
| **Insertar espacio entre el nombre de una declaración de función y la lista de parámetros** | `def X (): pass` | `def X(): pass` | 
| **Insertar espacio en paréntesis de lista de parámetros** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Insertar espacio en paréntesis de lista de parámetros vacía** | `def X( ): pass` | `def X(): pass` |
| **Insertar espacios alrededor de "=" en valores de parámetro predeterminados** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Insertar espacio antes y después de los operadores de anotación de valor devuelto** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opción de operadores | Activado | Borrado |
| --- | --- | --- |
| **Insertar espacios alrededor de operadores binarios** | `a + b` | `a+b` |
| **Insertar espacios alrededor de asignaciones** | `a = b` | `a=b` |

<br/>

| Opción de espaciado de expresión | Activado | Borrado |
| --- | --- | --- |
| **Insertar espacio entre el nombre de una llamada de función y la lista de argumentos** | `X ()` | `X()` |
| **Insertar espacio entre paréntesis vacíos de la lista de argumentos** | `X( )` | `X()` |
| **Insertar espacio entre paréntesis de la lista de argumentos** | `X( a, b )` | `X(a, b)` |
| **Insertar espacio en paréntesis de expresión** | `( a )` | `(a)` |
| **Insertar espacio en paréntesis de tupla vacía** | `( )` | `()` |
| **Insertar espacio en paréntesis de tupla** | `( a, b )` | `(a, b)` |
| **Insertar espacio entre corchetes vacíos** | `[ ]` | `[]` |
| **Insertar espacios entre corchetes de listas** | `[ a, b ]` | `[a, b]` |
| **Insertar espacio delante de corchete de apertura** | `x [i]` | `x[i]` |
| **Insertar espacio entre corchetes** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instrucciones

Las opciones de **instrucciones** controlan la reescritura automática de diversas instrucciones en varios formularios de Python.

| Opción | Antes de aplicar formato | Después de aplicar formato |
| --- | --- | --- |
| **Colocar módulos importados en nueva línea** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Quitar punto y coma innecesario** | `x = 42;` | `x = 42` |
| **Colocar varias instrucciones en las nuevas líneas** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Ajuste

**Ajuste** le permite establecer el **Ancho máximo del comentario** (el valor predeterminado es 80). Si la opción **Ajustar comentarios que son demasiado anchos** está activada, Visual Studio volverá a aplicar formato a los comentarios para no superar ese ancho máximo.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Comando Fill Comment Paragraph command (Rellenar párrafo de comentarios)

**Editar** > **Opciones avanzadas** > **Rellenar párrafo del comentario** (**Ctrl**+**E** > **P**) redistribuye el texto del comentario y le aplica formato, combinando líneas cortas y separando largas.

Por ejemplo:

```python
# foo
# bar
# baz
```

cambia a:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

cambia a:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
