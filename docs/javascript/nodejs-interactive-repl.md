---
title: Usar el REPL de Node.js
description: Visual Studio permite interactuar con el tiempo de ejecución de Node.js.
ms.custom: ''
ms.date: 12/04/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 7b980634a95c14413dd07649893a26b21de6f78d
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2018
ms.locfileid: "53442072"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Trabajar con la ventana interactiva de Node.js

Herramientas de Node.js para Visual Studio incluye una ventana interactiva para el tiempo de ejecución de Node.js instalado. En esta ventana se puede escribir código JavaScript y ver los resultados inmediatamente, así como ejecutar comandos npm para interactuar con el proyecto actual. La ventana interactiva también se conoce como REPL (**R**ead/**E**valuate/**P**rint **L**oop, es decir, bucle de lectura, evaluación e impresión).

## <a name="open-the-interactive-window"></a>Abrir la ventana interactiva

Para abrir la ventana interactiva, haga clic con el botón derecho en el nodo de proyecto Node.js en el Explorador de soluciones y seleccione **Abrir ventana interactiva de Node.js**.

![Ventana interactiva de Node.js en el menú contextual del proyecto](../javascript/media/interactivewindow-open-from-project.png)

Las teclas de método abreviado predeterminadas para abrir la ventana interactiva de Node.js son **[CTRL]+K, N**. La ventana también se puede abrir desde la barra de herramientas; para ello, seleccione **Vista** > **Ventanas** > **Ventana interactiva de Node.js**.

## <a name="use-the-repl"></a>Usar el REPL

Una vez abierta la ventana, puede escribir comandos.

![Ventana interactiva de Node.js](../javascript/media/interactivewindow.png)

La ventana interactiva tiene varios comandos integrados, que comienzan con un punto a modo de prefijo para distinguirlos de cualquier función JavaScript que declare. Se admiten los siguientes comandos:

**.cls, .clear** Borran el contenido de la ventana del editor, pero deja intactos el historial y el contexto de ejecución.

**.help** Muestra la Ayuda del comando especificado o de todos los comandos disponibles, así como los enlaces de teclado, si no se ha especificado ninguno.

**.info** Muestra información sobre el archivo ejecutable de Node.js que se usa actualmente.

**.npm** Se ejecuta como un comando npm. Si la solución contiene más de un proyecto, especifique el proyecto de destino mediante `.npm [projectname] <npm arguments>`.

**.reset** Restablece el entorno de ejecución al estado inicial, conservando el historial.

**.save** Guarda la sesión de REPL actual en un archivo.