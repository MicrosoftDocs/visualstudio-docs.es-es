---
title: Opciones, editor de texto, JavaScript, formato
description: Aprenda a usar la página Formato del cuadro de diálogo Opciones para establecer las opciones para la aplicación de formato al código en el Editor de código.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 27b2c5765f041252e62defd15a3c7b6d7b460b43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932467"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Cuadro de diálogo Opciones: Editor de texto \> JavaScript \> Formato

Use la página **Formato** del cuadro de diálogo **Opciones** para establecer las opciones para proporcionar formato al código en el Editor de código. Para acceder a esta página, en la barra de menús elija **Herramientas** > **Opciones** y expanda **Editor de texto** > **JavaScript/TypeScript** > **Formato**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Formato automático

Estas opciones determinan cuándo se da formato en la vista **Origen**.

### <a name="uielement-list"></a>Lista de UIElement

|Opción|Descripción|
|------------|-----------------|
|**Dar formato a una línea completada al presionar &Entrar**|Cuando se selecciona esta opción, el editor de código aplica formato a la línea automáticamente cuando presiona la tecla Entrar.|
|**Dar formato a una instrucción completada con ;**|Cuando se selecciona esta opción, el editor de código aplica formato a la línea automáticamente cuando presiona la tecla de punto y coma.|
|**Dar formato a un bloque abierto con {**|Cuando esta opción está seleccionada, el editor de código aplica formato automáticamente a la línea cuando se presiona la tecla de llave de apertura.|
|**Dar formato a un bloque completado con }**|Cuando se selecciona esta opción, el editor de código aplica formato a la línea automáticamente cuando presiona la tecla de llave de cierre.|
|**Dar formato al pegar**|Cuando se selecciona esta opción, el Editor de código cambia el formato del código cuando lo pega en el editor. El editor usa las reglas de formato definidas actualmente. Si no se selecciona esta opción, el editor usa el formato original del código pegado.|

## <a name="new-lines"></a>Nuevas líneas

Estas opciones determinan si el editor de código coloca una llave de apertura para funciones y bloques de control en una nueva línea.

### <a name="uielement-list"></a>Lista de UIElement

|Opción|Descripción|
|------------|-----------------|
|**Colocar llave de apertura en línea nueva para funciones**|Cuando se selecciona esta opción, el editor de código desplaza la llave de apertura asociada a una función a una nueva línea.|
|**Colocar llave de apertura para bloques de control en nueva línea**|Cuando se selecciona esta opción, el editor de código desplaza la llave de apertura asociada a un bloque de control (por ejemplo, los bloques de control `if` y `while`) a una nueva línea.|

## <a name="spacing"></a>Espaciado

Estas opciones determinan cómo se insertan los espacios en la vista **Origen**.

### <a name="uielement-list"></a>Lista de UIElement

|Opción|Descripción|
|------------|-----------------|
|**Insertar espacio después del delimitador de coma**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de delimitadores de coma.|
|**Insertar espacio tras punto y coma en instrucciones "for"**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de cada punto y coma en la primera línea de un bucle `for`.|
|**Insertar espacio delante y detrás de operadores binarios**|Cuando se selecciona esta opción, el editor de código agrega un espacio antes y después de los operadores binarios (por ejemplo, +, -, &&, &#124;&#124;).|
|**Insertar espacio después de palabras clave en instrucciones de flujo de control**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de palabras clave de JavaScript en las instrucciones de flujo de control.|
|**Insertar espacio tras la palabra clave function para las funciones anónimas**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de la palabra clave `function` para funciones anónimas.|
|**Insertar espacio después de abrir y antes de cerrar paréntesis con contenido**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de los paréntesis de apertura y antes de los paréntesis de cierre si dentro de los paréntesis hay caracteres con contenido.|

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)