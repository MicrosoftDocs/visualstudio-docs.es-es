---
title: "Formato del código de Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0f1631-360b-45d4-a0cb-01c3c10d25f2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: b9e1c2b6be671adb99a13e4a0eb4357fbba477b2
ms.lasthandoff: 04/10/2017

---

# <a name="formatting-python-code"></a>Formato de código de Python

Visual Studio permite volver a aplicar formato rápidamente al código para que coincida con las opciones de formato configuradas previamente.

- Para aplicar formato a una selección: seleccione **Edit > Advanced > Format Selection** (Editar > Opciones avanzadas > Aplicar formato a selección) o presione Ctrl+E,F.
- Para aplicar formato a todo el archivo: seleccione **Edit > Advanced > Format Document** (Editar > Opciones avanzadas > Aplicar formato a documento) o presione Ctrl+E,D.

Las opciones se establecen mediante **Tools > Options > Text Editor > Python > Formatting** (Herramientas > Opciones > Editor de texto > Python > Aplicar formato) y sus pestañas secundarias; de forma predeterminada, se configuran para que coincidan con un superconjunto de la [guía de estilo de PEP 8](http://www.python.org/dev/peps/pep-0008/). La pestaña **General** determina cuándo se aplica el formato; las otras tres subpáginas se definen en las secciones siguientes.

La compatibilidad con Python en Visual Studio también agrega el práctico comando [Rellenar párrafo del comentario](#fill-comment-paragraph-command) al menú **Editar > Opciones avanzadas**, como se describe a continuación.

## <a name="spacing"></a>Espaciado

El **espaciado** controla dónde se insertan o quitan los espacios en torno a diversas construcciones de lenguajes. Cada opción tiene tres valores posibles:

- Activada: garantiza que se aplica el espaciado.
- Desactivada: elimina el espaciado.
- Indeterminada: deja el formato original en su sitio.

En las tablas siguientes se proporcionan ejemplos de las distintas opciones.

| Opción de definiciones de clase | Activado | Borrado |
| --- | --- | --- | 
| Insertar espacio entre el nombre de la declaración de clase y la lista de bases | `class X (object): pass` | `class X(object): pass` | 
| Insertar espacio en paréntesis de lista de bases | `class X( object ): pass` | `class X(object): pass` |
| Insertar espacio en paréntesis de lista de bases vacía | `class X( ): pass` | `class X(): pass` |

<br/>

| Opción de definiciones de función | Activado | Borrado |
| --- | --- | --- |
| Insertar espacio entre el nombre de una declaración de función y la lista de parámetros | `def X (): pass` | `def X(): pass` | 
| Insertar espacio en paréntesis de lista de parámetros | `def X( a, b ): pass` | `def X(a, b): pass` |
| Insertar espacio en paréntesis de lista de parámetros vacía | `def X( ): pass` | `def X(): pass` |
| Insertar espacios alrededor de '=' en valores de parámetro predeterminados | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Insertar espacio antes y después de los operadores de anotación de valor devuelto | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opción de operadores | Activado | Borrado |
| --- | --- | --- |
| Insertar espacios alrededor de operadores binarios | `a + b` | `a+b` |
| Insertar espacios alrededor de asignaciones | `a = b` | `a=b` |

<br/>

| Opción de espaciado de expresión | Activado | Borrado |
| --- | --- | --- |
| Insertar espacio entre el nombre de una llamada de función y la lista de argumentos | `X ()` | `X()` |
| Insertar espacio entre paréntesis vacíos de la lista de argumentos | `X( )` | `X()` |
| Insertar espacio entre paréntesis de la lista de argumentos | `X( a, b )` | `X(a, b)` |
| Insertar espacio en paréntesis de expresión | `( a )` | `(a)` |
| Insertar espacio en paréntesis de tupla vacía | `( )` | `()` |
| Insertar espacio en paréntesis de tupla | `( a, b )` | `(a, b)` |
| Insertar espacio entre corchetes vacíos | `[ ]` | `[]` |
| Insertar espacios entre corchetes de listas | `[ a, b ]` | `[a, b]` |
| Insertar espacio delante de corchete de apertura | `x [i]` | `x[i]` |
| Insertar espacio entre corchetes | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instrucciones

Las **instrucciones** controlan la reescritura automática de diversas instrucciones en varios formularios de Python.

| Opción | Antes de aplicar formato | Después de aplicar formato |
| --- | --- | --- |
| Colocar módulos importados en nueva línea | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Quitar punto y coma innecesario | `x = 42;` | `x = 42` |
| Colocar varias instrucciones en las nuevas líneas | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |


## <a name="wrapping"></a>Ajuste

El **ajuste** permite establecer el **ancho máximo del comentario** (el valor predeterminado es 80), de modo que si la opción **Ajustar comentarios que son demasiado anchos** está activada, Visual Studio volverá a aplicar formato a los comentarios para no superar ese ancho.

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

**Edit > Advanced > Fill Comment Paragraph** (Editar > Opciones avanzadas > Rellenar párrafo de comentarios) (Ctrl+E,Ctrl+P). Este comando redistribuye y aplica formato al texto de comentario, y combina líneas cortas y otras más largas separadas.

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
