---
title: Ventana Comandos
description: Obtenga información sobre cómo puede usar la ventana Comandos para ejecutar comandos o alias directamente en el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fba1c12743035c397780db64939dec8195a75afd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942859"
---
# <a name="command-window"></a>Ventana de comandos
La ventana **Comandos** se usa para ejecutar comandos o alias directamente en el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Puede ejecutar comandos de menú y comandos que no aparecen en ningún menú. Para mostrar la ventana **Comandos**, pulse **Otras ventanas** desde el menú **Ver** y seleccione **Ventana Comandos**.

## <a name="displaying-the-values-of-variables"></a>Mostrar los valores de las variables
Para comprobar el valor de una variable `varA`, use el [comando Imprimir](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

El signo de interrogación (?) es un alias de `Debug.Print`, por lo que este comando también puede escribirse:

```cmd
>? varA
```

Ambas versiones de este comando devolverán el valor de la variable `varA`.

## <a name="entering-commands"></a>Escribir comandos
El signo de mayor que (`>`) aparece en el borde izquierdo de la ventana Comandos como un aviso para las líneas nuevas. Use las teclas FLECHA ARRIBA y FLECHA ABAJO para desplazarse por los comandos ejecutados anteriormente.

|Tarea|Solución|Ejemplo|
|----------|--------------|-------------|
|Evaluar una expresión.|Comenzar la expresión con un signo de interrogación (`?`).|`? myvar`|
|Cambiar a una ventana Inmediato.|Escribir `immed` en la ventana sin el signo de mayor que (>)|`immed`|
|Cambiar de nuevo a la ventana Comandos desde una ventana Inmediato.|Escribir `cmd` en la ventana.|`>cmd`|

Los siguientes accesos directos le ayudan a navegar mientras esté en el modo de comando.

|Acción|Ubicación del cursor|Enlace de teclado|
|------------| - |----------------|
|Desplazarse por la lista de los comandos especificados anteriormente.|Línea de entrada|FLECHA ARRIBA y FLECHA ABAJO|
|Desplazar hacia arriba la ventana.|Contenido de la ventana Comandos|CTRL+FLECHA ARRIBA|
|Desplazar hacia abajo la ventana.|Contenido de la ventana Comandos|FLECHA ABAJO o CTRL+FLECHA ABAJO|

> [!TIP]
> Puede copiar todo o una parte del comando anterior en la línea de entrada desplazándose hasta él, resaltando todo o una parte de este y, después, presionando ENTRAR.

## <a name="mark-mode"></a>Modo Marcar
Cuando hace clic en cualquier línea anterior de la ventana **Comandos**, cambia automáticamente al modo Marcar. Esto le permite seleccionar, editar y copiar el texto de los comandos anteriores como lo haría en cualquier editor de texto, y pegarlo en la línea actual.

## <a name="the-equals--sign"></a>El signo igual (=)
La ventana que se usa para escribir el comando `EvaluateStatement` determina si el signo igual (=) se interpreta como un operador de comparación o como un operador de asignación.

En la ventana **Comandos**, un signo igual (=) se interpreta como un operador de comparación. No puede usar operadores de asignación en la ventana **Comandos**. Por tanto, por ejemplo, si los valores de las variables `varA` y `varB` son diferentes, entonces el comando `>Debug.EvaluateStatement(varA=varB)` devolverá un valor de `False`.

En la ventana **Inmediato**, por el contrario, un signo igual (=) se interpreta como un operador de asignación. Por ejemplo, el comando `>Debug.EvaluateStatement(varA=varB)` asignará a la variable `varA` el valor de la variable `varB`.

## <a name="parameters-switches-and-values"></a>Parámetros, modificadores y valores
Algunos comandos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tienen valores, modificadores y argumentos opcionales y necesarios. Determinadas reglas se aplican al tratar con dichos comandos. A continuación se muestra un ejemplo de un comando enriquecido para aclarar la terminología.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

En este ejemplo,

- `Edit.ReplaceInFiles` es el comando

- `/case` y `/pattern:regex` son modificadores (comienzan por el carácter de barra diagonal [/])

- `regex` es el valor del modificador `/pattern`; el modificador `/case` no tiene valor

- `var[1-3]+` y `oldpar` son parámetros

    > [!NOTE]
    > Cualquier comando, parámetro, modificador o valor que contenga espacios debe tener comillas dobles a cada lado.

La posición de los modificadores y parámetros puede intercambiarse de manera libre en la línea de comandos con la excepción del comando [Shell](../../ide/reference/shell-command.md), que necesita sus modificadores y parámetros en un orden específico.

Prácticamente cada modificador que admite un comando tiene dos formatos: un formato corto (un carácter) y un formato largo. Pueden combinarse varios modificadores de formato corto en un grupo. Por ejemplo, `/p /g /m` puede expresarse de manera alternativa como `/pgm`.

Si los modificadores de formato corto se combinan en un grupo y se les proporciona un valor, ese valor se aplica a cada modificador. Por ejemplo, `/pgm:123` equivale a `/p:123 /g:123 /m:123`. Se produce un error si cualquiera de los modificadores del grupo no acepta un valor.

## <a name="escape-characters"></a>Caracteres de escape
Un carácter de intercalación (^) en una línea de comandos significa que el carácter que le sigue se interpreta literalmente, en lugar de interpretarse como un carácter de control. Esto se puede usar para insertar comillas rectas ("), espacios, barras diagonales iniciales, símbolos de intercalación o cualquier otro carácter literal en un valor de parámetro o modificador, con la excepción de los nombres de los modificadores. Por ejemplo,

```cmd
>Edit.Find ^^t /regex
```

El símbolo de intercalación funciona igual tanto si está dentro como fuera de unas comillas. Si el símbolo de intercalación es el último carácter de la línea, se ignora. En el ejemplo que se muestra aquí se muestra cómo buscar el patrón "^t".

## <a name="use-quotes-for-path-names-with-spaces"></a>Usar comillas para los nombres de ruta con espacios
Si, por ejemplo, quiere abrir un archivo que tiene una ruta que contiene espacios, debe colocar comillas alrededor de la ruta o del segmento de ruta que contiene espacios: **C:\\"Archivos de programa"** o **"C:\Archivos de programa"**.

## <a name="see-also"></a>Consulte también

- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
