---
title: Cuadro Buscar/Comando
description: Aprenda sobre el cuadro Buscar/Comando y cómo puede usarlo para buscar texto y ejecutar comandos de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 341362fe74d4d8a6edbf10afec1a0d49998e857d
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006606"
---
# <a name="findcommand-box"></a>Buscar/Comando (cuadro)

Puede buscar texto y ejecutar comandos de Visual Studio desde el cuadro **Buscar comando**. El cuadro **Comando/Buscar** todavía está disponible como un control de la barra de herramientas, pero ya está visible de manera predeterminada. Puede mostrar el cuadro **Comando/Buscar** pulsando **Agregar o quitar botones** en la barra de herramientas **Estándar** y, después, pulsar **Buscar**.

Para ejecutar un comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], precédalo de un signo mayor que ( **>** ).

El cuadro **Buscar comando** conserva los últimos 20 elementos escritos y los muestra en una lista desplegable. Puede navegar por la lista con las **teclas de dirección**.

![Cuadro Buscar&#47;Comando](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Buscar texto

Cuando se especifica texto en el cuadro **Buscar comando** y se presiona la tecla **ENTRAR**, Visual Studio busca de forma predeterminada la ventana de herramientas o documento actuales con las opciones especificadas en el cuadro de diálogo **Buscar en archivos**. Para obtener más información, vea [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Escribir comandos

Para usar el cuadro **Buscar comando** para emitir un solo comando o alias de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en lugar de buscar texto, escriba el comando precedido de un signo mayor que (**>**). Por ejemplo:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

También puede usar la ventana **Comandos** para escribir y ejecutar uno o varios comandos. Algunos comandos o alias pueden escribirse y ejecutarse por sí solos; otros requieren argumentos en su sintaxis. Para obtener una lista de los comandos que tienen argumentos, vea [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Carácter de escape

Un carácter de intercalación ( **^** ) en un comando significa que el carácter que le sigue se interpreta literalmente, en lugar de interpretarse como un carácter de control. Esto se puede usar para insertar comillas rectas (**"**), espacios, barras diagonales iniciales, símbolos de intercalación o cualquier otro carácter literal en un valor de parámetro o modificador, con la excepción de los nombres de los modificadores. Por ejemplo:

```
>Edit.Find ^^t /regex
```

El símbolo de intercalación funciona igual tanto si está dentro como fuera de unas comillas. Si el símbolo de intercalación es el último carácter de la línea, se ignora.

## <a name="see-also"></a>Consulte también

- [Ventana Comandos](../ide/reference/command-window.md)
- [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)
