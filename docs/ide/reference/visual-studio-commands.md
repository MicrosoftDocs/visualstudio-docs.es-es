---
title: Comandos
description: Obtenga información sobre los distintos comandos a los que tiene acceso en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7928c03e52e4a72fb354bd7202e041ec2264fcd6
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560959"
---
# <a name="visual-studio-commands"></a>Comandos de Visual Studio

Puede escribir comandos de Visual Studio en la ventana **Comando**, la ventana **Inmediato** o el cuadro **Buscar/Comando**. En todos los casos, el signo mayor que (`>`) indica que se debe seguir un comando en lugar de una operación de búsqueda o de depuración.

Encontrará una lista completa de los comandos y su sintaxis en la página **Teclado** de **Herramientas** > **Opciones** > **Entorno**.

En las versiones localizadas del IDE, los nombres de los comandos se pueden escribir en el idioma nativo del IDE o en inglés. Por ejemplo, puede escribir `File.NewFile` o `Fichier.NouveauFichier` en el IDE francés para ejecutar el mismo comando.

Muchos comandos tienen alias. Para obtener una lista de alias de comandos, consulte [Alias de comandos](../../ide/reference/visual-studio-command-aliases.md). Para ver los métodos abreviados de teclado de comandos, vea [Métodos abreviados de teclado predeterminados de Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Carácter de escape

El carácter de escape para los comandos de Visual Studio es un símbolo de intercalación (^). El carácter de escape significa que el carácter que le sigue se interpreta literalmente, en lugar de interpretarse como un carácter de control. Esto se puede usar para insertar comillas rectas ("), espacios, barras diagonales iniciales, símbolos de intercalación o cualquier otro carácter literal en un valor de parámetro o modificador, con la excepción de los nombres de los modificadores. Por ejemplo:

```
>Edit.Find ^^t /regex
```

El símbolo de intercalación funciona igual tanto si está dentro como fuera de unas comillas. Si el símbolo de intercalación es el último carácter de la línea, se omite.

## <a name="commands-with-arguments"></a>Comandos con argumentos

Los siguientes comandos toman argumentos o modificadores:

| Nombre de comando | Descripción |
| - | - |
| [Agregar elemento existente](../../ide/reference/add-existing-item-command.md) | Agrega un archivo existente a la solución actual y lo abre. |
| [Agregar proyecto existente](../../ide/reference/add-existing-project-command.md) | Agrega un proyecto existente a la solución actual. |
| [Agregar nuevo elemento](../../ide/reference/add-new-item-command.md) | Agrega un nuevo elemento de solución (como un archivo .htm, .css o .txt o un conjunto de marcos) a la solución actual y lo abre. |
| [Alias](../../ide/reference/alias-command.md) | Crea un nuevo alias para un comando completo, un comando completo con argumentos o incluso otro alias. |
| [Evaluar instrucción](../../ide/reference/evaluate-statement-command.md) | Evalúa y muestra la instrucción dada. |
| [Buscar](../../ide/reference/find-command.md) | Busca archivos empleando un subconjunto de las opciones disponibles en el control **Buscar y reemplazar** . |
| [Buscar en archivos](../../ide/reference/find-in-files-command.md) | Busca archivos empleando un subconjunto de las opciones disponibles en el control [Buscar en archivos](../../ide/find-in-files.md). |
| [Ir a](../../ide/reference/go-to-command.md) | Mueve el cursor a la línea especificada. |
| [Mostrar pila de llamadas](../../ide/reference/list-call-stack-command.md) | Muestra la pila de llamadas actual. |
| [Mostrar desensamblado](../../ide/reference/list-disassembly-command.md) | Inicia el proceso de depuración y le permite especificar cómo se deben tratar los errores. |
| [Mostrar memoria](../../ide/reference/list-memory-command.md) | Muestra el contenido del intervalo de memoria especificado. |
| [Mostrar módulos](../../ide/reference/list-modules-command.md) | Enumera los módulos del proceso actual. |
| [Mostrar registros](../../ide/reference/list-registers-command.md) | Muestra una lista de registros. |
| [Mostrar código fuente](../../ide/reference/list-source-command.md) | Muestra las líneas de código fuente especificadas. |
| [Mostrar subprocesos](../../ide/reference/list-threads-command.md) | Muestra una lista de los subprocesos del programa actual. |
| [Registrar resultados de la ventana Comandos](../../ide/reference/log-command-window-output-command.md) | Copia en un archivo todas las entradas y salidas de la ventana Comando. |
| [Nuevo archivo](../../ide/reference/new-file-command.md) | Crea un nuevo archivo y lo agrega al proyecto seleccionado. |
| [Abrir archivo](../../ide/reference/open-file-command.md) | Abre un archivo existente y le permite especificar un editor. |
| [Abrir proyecto](../../ide/reference/open-project-command.md) | Abre un proyecto existente y le permite agregar el proyecto a la solución actual. |
| [Imprimir](../../ide/reference/print-command.md) | Evalúa la expresión y muestra los resultados o el texto especificado. |
| [Inspección rápida (Comando)](../../ide/reference/quick-watch-command.md) | Muestra el texto seleccionado o especificado en el campo **Expresión** del cuadro de diálogo **Inspección rápida** . |
| [Sustituya](../../ide/reference/replace-command.md) | Reemplaza texto de los archivos empleando un subconjunto de las opciones disponibles en el control **Buscar y reemplazar** . |
| [Reemplazar en archivos](../../ide/reference/replace-in-files-command.md) | Reemplaza texto de los archivos empleando un subconjunto de las opciones disponibles en [Reemplazar en archivos](../../ide/replace-in-files.md). |
| [Establecer marco de pila actual](../../ide/reference/set-current-stack-frame-command.md) | Le permite ver un marco de pila determinado. |
| [Establecer subproceso actual](../../ide/reference/set-current-thread-command.md) | Le permite ver un subproceso determinado. |
| [Establecer base](../../ide/reference/set-radix-command.md) | Determina el número de bytes que se van a ver. |
| [Shell](../../ide/reference/shell-command.md) | Inicia programas desde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] como si el comando se hubiera ejecutado desde el símbolo del sistema. |
| [ShowWebBrowser (Comando)](../../ide/reference/showwebbrowser-command.md) | Muestra la dirección URL especificada en una ventana del explorador web dentro o fuera del entorno de desarrollo integrado (IDE). |
| [Iniciar](../../ide/reference/start-command.md) | Inicia el proceso de depuración y le permite especificar cómo se deben tratar los errores. |
| [Path](../../ide/reference/symbol-path-command.md) | Establece la lista de directorios para que el depurador busque símbolos. |
| [Alternar punto de interrupción](../../ide/reference/toggle-breakpoint-command.md) | Activa o desactiva el punto de interrupción, en función del estado actual, en la ubicación actual del archivo. |
| [Inspección (Comando)](../../ide/reference/watch-command.md) | Crea y abre una instancia especificada de una ventana **Inspección** . |

## <a name="see-also"></a>Consulte también

- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
