---
title: Opciones, Editor de texto, Todos los lenguajes
description: Obtenga información sobre cómo usar la página General de la sección Todos los lenguajes para cambiar el comportamiento predeterminado del editor de código en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b507f79aa4afb1bd5d2f56893d2e32aae0db4c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905579"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Cuadro de diálogo Opciones: Editor de texto \> Todos los lenguajes

Este cuadro de diálogo le permite cambiar el comportamiento predeterminado del Editor de código. Estas opciones también se aplican a otros editores basados en el Editor de código, como la vista de origen del diseñador HTML. Para abrir este cuadro de diálogo, seleccione **Opciones** del menú **Herramientas**. En la carpeta **Editor de texto**, expanda la subcarpeta **Todos los lenguajes** y, después, pulse **General**.

> [!CAUTION]
> Esta página establece las opciones predeterminadas de todos los lenguajes de desarrollo. Recuerde que restablecer una opción en este cuadro de diálogo restablecerá las opciones generales de todos los lenguajes para cualquier elección seleccionada aquí. Para cambiar las opciones del Editor de texto solo de un lenguaje, expanda la subcarpeta de ese lenguaje y seleccione sus páginas de opciones.

Se muestra una marca atenuada cuando se ha seleccionado una opción en las páginas de opciones generales para algunos lenguajes de programación, pero no para otros.

## <a name="statement-completion"></a>Finalización de instrucciones

**Lista de miembros automática**

Cuando está seleccionada, IntelliSense muestra las listas emergentes de miembros disponibles, propiedades, valores o métodos a medida que escribe en el editor. Elija cualquier elemento de la lista emergente para insertarlo en el código. Al seleccionar esta opción se habilita la opción **Ocultar miembros avanzados**.

**Ocultar miembros avanzados**

Cuando está seleccionada, se acortan las listas emergentes de finalización de instrucciones mostrando solo los elementos que más se usan. Los demás elementos se extraen de la lista.

**Información del parámetro**

Cuando está seleccionada esta casilla, la sintaxis completa del procedimiento o la declaración actual se muestra en el punto de inserción del editor, con todos los parámetros disponibles. El siguiente parámetro que puede asignar aparece en negrita.

## <a name="settings"></a>Configuración

**Habilitar espacio virtual**

Cuando esta opción está seleccionada y la casilla **Ajuste de línea** se desactiva, puede hacer clic en cualquier parte más allá del final de una línea en el Editor de código y escribir. Esta característica puede usarse para colocar los comentarios en un lugar coherente junto al código.

**Ajuste de línea**

Cuando está seleccionada, cualquier parte de una línea que se extienda horizontalmente más allá del área visible del editor aparecerá automáticamente en la siguiente línea. Al activar esta opción se habilita la opción **Mostrar glifos visuales para ajuste de línea**.

> [!NOTE]
> La característica **Espacio virtual** se desactiva mientras **Ajuste de línea** está activada.

**Mostrar glifos visuales para ajuste de línea**

Cuando está seleccionada, se muestra un indicador de flecha de retorno en el que una línea larga se ajusta en una segunda línea.

![Captura de pantalla de LineBreakSymbol](../../ide/reference/media/linebreak.gif)

Desactive esta casilla si prefiere no mostrar estos indicadores.

> [!NOTE]
> Estas flechas de aviso no se agregan al código ni se imprimen. Solo sirven como referencia.

**Números de línea**

Cuando está seleccionada, aparece un número de línea junto a cada línea de código.

> [!NOTE]
> Estos números de línea no se agregan al código ni se imprimen. Solo sirven como referencia.

**Habilitar acceso a direcciones URL con un solo clic**

Si está seleccionada, el cursor del mouse pasa a ser una mano cuando se sitúe sobre una dirección URL en el editor. Puede hacer clic en la dirección URL para mostrar la página indicada en el explorador web.

**Barra de navegación**

Cuando está seleccionada, muestra la **Barra de navegación** en la parte superior del editor de código. Sus listas desplegables **Objetos** y **Miembros** le permiten elegir un objeto determinado en su código, seleccionar desde sus miembros e ir a la declaración del miembro seleccionado en el Editor de código.

**Aplicar los comandos Cortar o Copiar a las líneas en blanco cuando no haya selección**

Esta opción establece el comportamiento del editor cuando se coloca el punto de inserción en una línea en blanco, no se selecciona nada y, después, se usa el comando Copiar o Cortar.

- Cuando se selecciona esta opción, se copia o se corta la línea en blanco. Si después ejecuta Pegar, se inserta una línea en blanco nueva.

- Cuando esta opción está desactivada, el comando Cortar quita las líneas en blanco. En cambio, los datos del Portapapeles se conservan. Por lo tanto, si después usa el comando Pegar, se pega el contenido copiado en último lugar en el Portapapeles. Si previamente no se ha copiado nada, no se pegará nada.

Esta opción no tiene ningún efecto en el comando Copiar o Cortar cuando la línea no está en blanco. Si no se selecciona nada, se copia o se corta la línea entera. Si se pega después, se pega el texto de toda la línea y el carácter de fin de línea.

> [!TIP]
> Con el fin de poder mostrar indicadores para los espacios, tabuladores y fines de la línea, y distinguir así las líneas con sangría de las que están completamente en blanco, en el menú **Edición** seleccione **Opciones avanzadas** y pulse **Ver espacios en blanco**.

## <a name="see-also"></a>Consulte también

- [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
- [Usar IntelliSense](../../ide/using-intellisense.md)
