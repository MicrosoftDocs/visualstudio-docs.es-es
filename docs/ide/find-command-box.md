---
title: Cuadro Buscar/Comando
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 221c5fbbd3f0f82ac97d0c2a0fcc82657e0296c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977803"
---
# <a name="findcommand-box"></a>Buscar/Comando (cuadro)

Puede buscar texto y ejecutar comandos de Visual Studio desde el cuadro **Buscar comando**. El cuadro **Comando/Buscar** todavía está disponible como un control de la barra de herramientas, pero ya está visible de manera predeterminada. Puede mostrar el cuadro **Comando/Buscar** pulsando **Agregar o quitar botones** en la barra de herramientas **Estándar** y, después, pulsar **Buscar**.

Para ejecutar un comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], precédalo de un signo mayor que (**>**).

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

## <a name="escape-characters"></a>Caracteres de escape

Un carácter de intercalación (**^**) en un comando significa que el carácter que le sigue se interpreta literalmente, en lugar de interpretarse como un carácter de control. Esto se puede usar para insertar comillas rectas (**"**), espacios, barras diagonales iniciales, símbolos de intercalación o cualquier otro carácter literal en un valor de parámetro o modificador, con la excepción de los nombres de los modificadores. Por ejemplo:

```
>Edit.Find ^^t /regex
```

El símbolo de intercalación funciona igual tanto si está dentro como fuera de unas comillas. Si el símbolo de intercalación es el último carácter de la línea, se ignora.

## <a name="see-also"></a>Vea también

- [Ventana Comandos](../ide/reference/command-window.md)
- [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)