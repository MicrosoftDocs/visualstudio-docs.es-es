---
title: Inmediato (ventana)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b18e1837fdc673500fae96555dab7fb0195ec42e
ms.sourcegitcommit: 9866740aec05d1a3a5dc3b4b6d2ceaeecbd3fc29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2019
ms.locfileid: "55424245"
---
# <a name="immediate-window"></a>Inmediato (ventana)

La ventana **Inmediato** sirve para depurar y evaluar expresiones, ejecutar instrucciones, imprimir valores de variables, etc. Permite escribir expresiones para evaluarlas o ejecutarlas mediante el lenguaje de desarrollo durante la depuración.

Para mostrar la ventana **Inmediato**, abra un proyecto para editarlo, elija **Depurar** > **Ventanas** > **Inmediato** o presione **Ctrl**+**Alt**+**I**. También puede escribir **Debug.Immediate** en la ventana **Comandos**.

Puede usar la ventana **Inmediato** para emitir comandos individuales de Visual Studio. Entre los comandos disponibles se incluye `EvaluateStatement`, que puede usarse para asignar valores a variables. La ventana **Inmediato** también admite IntelliSense.

## <a name="display-the-values-of-variables"></a>Mostrar los valores de variables

La ventana **Inmediato** puede resultar particularmente útil al depurar una aplicación. Por ejemplo, para comprobar el valor de una variable `varA`, usar el [comando Imprimir](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

El signo de interrogación (?) es un alias de `Debug.Print`, por lo que este comando también puede escribirse:

```cmd
>? varA
```

Ambas versiones de este comando devuelven el valor de la variable `varA`.

> [!TIP]
> Para emitir un comando de Visual Studio en la ventana **Inmediato**, este debe ir precedido por un signo mayor que (>). Para escribir varios comandos, cambie a la ventana **Comando**.

## <a name="design-time-expression-evaluation"></a>Evaluación de expresiones en tiempo de diseño

Puede usar la ventana **Inmediato** para ejecutar una función o subrutina en tiempo de diseño.

### <a name="execute-a-function-at-design-time"></a>Ejecutar una función en tiempo de diseño

1. Copie el código siguiente en una aplicación de consola [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. En el menú **Depurar**, haga clic en **Ventanas** y en **Inmediato**.

3. Escriba `?MyFunction(2)` en la ventana **Inmediato** y presione **Entrar**.

    La ventana **Inmediato** ejecuta `MyFunction` y muestra `4`.

Si la función o subrutina contiene un punto de interrupción, Visual Studio interrumpe la ejecución en el punto adecuado. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Para más información, vea [Tutorial: Depuración en tiempo de diseño](../../debugger/walkthrough-debugging-at-design-time.md).

No puede usar la evaluación de expresiones en tiempo de diseño en los tipos de proyectos que requieren que se inicie un entorno de ejecución, incluidos los proyectos de [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)], proyectos web, proyectos de Smart Device y proyectos de SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Evaluación de expresiones en tiempo de diseño en soluciones de varios proyectos

Al establecer el contexto de evaluación de expresiones en tiempo de diseño, Visual Studio hace referencia al proyecto seleccionado actualmente en Explorador de soluciones. Si no se selecciona ningún proyecto en Explorador de soluciones, Visual Studio intenta evaluar la función en el proyecto de inicio. Si no se puede evaluar la función en el contexto actual, recibirá un mensaje de error. Si está intentando evaluar una función en un proyecto que no es el proyecto de inicio para la solución y recibe un error, pruebe a seleccionar el proyecto en el Explorador de soluciones e intente realizar la evaluación otra vez.

## <a name="enter-commands"></a>Especificar comandos

Escriba el signo mayor que (>) al emitir comandos de Visual Studio en la ventana **Inmediato**. Use las teclas **Flecha arriba** y **Flecha abajo** para desplazarse por los comandos emitidos anteriormente.

|Tarea|Soluciones|Ejemplo|
|----------|--------------|-------------|
|Evaluar una expresión.|Empezar la expresión con un signo de interrogación (?).|`? a+b`|
|Entrar temporalmente en el modo Comando mientras está en el modo Inmediato (para ejecutar un único comando).|Escribir el comando, precedido de un signo mayor que (>).|`>alias`|
|Cambiar a la ventana Comandos.|Escribir `cmd` en la ventana, precedido de un signo mayor que (>).|`>cmd`|
|Volver a la ventana Inmediato.|Escribir `immed` en la ventana sin el signo mayor que (>).|`immed`|

## <a name="mark-mode"></a>Modo Marcar

Cuando hace clic en cualquier línea anterior de la ventana **Inmediato**, cambia automáticamente al modo Marcar. Esto le permite seleccionar, editar y copiar el texto de los comandos anteriores como lo haría en cualquier editor de texto, y pegarlo en la línea actual.

## <a name="the-equals-sign-"></a>Signo igual (=)

La ventana que se usa para escribir el comando `EvaluateStatement` determina si el signo igual (=) se interpreta como un operador de comparación o como un operador de asignación.

En la ventana **Inmediato**, un signo igual (=) se interpreta como un operador de asignación. Por lo tanto, por ejemplo, el comando

```cmd
>Debug.EvaluateStatement(varA=varB)
```

asigna a la variable `varA` el valor de la variable `varB`.

Por el contrario, en la ventana **Comando**, un signo igual (=) se interpreta como un operador de comparación. No puede usar operaciones de asignación en la ventana **Comando**. Por lo tanto, por ejemplo, si los valores de las variables `varA` y `varB` son diferentes, entonces el comando

```cmd
>Debug.EvaluateStatement(varA=varB)
```

, devuelve un valor de `False`.

## <a name="first-chance-exception-notifications"></a>Notificaciones de excepciones de primera oportunidad

En algunas configuraciones, se muestran notificaciones de excepciones de primera oportunidad en la ventana **Inmediato**.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Activar o desactivar notificaciones de excepciones de primera oportunidad en la ventana Inmediato

1. En el menú **Vista**, haga clic en **Otras ventanas** y en **Salida**.

2. Haga clic con el botón derecho en el área de texto de la ventana **Salida** y active o desactive **Mensajes de excepción**.

## <a name="see-also"></a>Vea también

- [Desplazarse por el código con el depurador](../../debugger/navigating-through-code-with-the-debugger.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Primer vistazo al depurador](../../debugger/debugger-feature-tour.md)
- [Tutorial: Depuración en tiempo de diseño](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Usar expresiones regulares en Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
