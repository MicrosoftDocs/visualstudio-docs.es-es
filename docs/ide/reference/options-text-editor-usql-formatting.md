---
title: Opciones de formato del editor de U-SQL
description: Obtenga información sobre cómo usar la página de opciones Formato y sus subpáginas para establecer las opciones de formato del código en el editor de código cuando programa en U-SQL.
ms.custom: SEO-VS-2020
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a42fa7e5f40f413f7bc336ba8f0afbba7bdbf445
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932298"
---
# <a name="options-text-editor-u-sql-formatting"></a>Opciones, Editor de texto, U-SQL, formato

Use la página de opciones **Formato** para establecer las opciones de formato de código en el editor de código. Para acceder a esta página de opciones, elija **Herramientas** > **Opciones**. En el cuadro de diálogo **Opciones**, elija **Editor de texto** > **U-SQL** > **Formato**.

## <a name="general-page"></a>Página General

### <a name="general-settings"></a>Configuración general

Esta configuración afecta al *momento* en que el editor de código aplica las opciones de formato al código.

- **Dar formato automáticamente a las instrucciones completadas al escribir un punto y coma**

   Cuando se selecciona esta opción, se aplica formato a las instrucciones cuando elige la tecla de punto y coma según las opciones de formato seleccionadas para el editor.

- **Dar formato automáticamente al pegar**

   Si está activada, da formato al texto pegado en el editor para ajustarlo a las opciones de formato seleccionadas para el editor.

## <a name="preview-windows"></a>Ventanas de vista previa

Cada una de las subpáginas **Sangría**, **Nuevas líneas** y **Espaciado** muestra una ventana de vista previa en la parte inferior. La ventana de vista previa muestra el efecto de cada opción. Para usar la ventana de vista previa, seleccione una opción de formato. La ventana de vista previa muestra un ejemplo de la opción seleccionada. Cuando cambia la configuración (ya sea activando o desactivando una casilla), la ventana de vista previa se actualiza para mostrar el efecto de la nueva configuración.

### <a name="indentation-remarks"></a>Comentarios de sangría

Las opciones de sangría en las páginas **Pestañas** de cada idioma solo determinan dónde coloca el cursor el Editor de código cuando se presiona **Entrar** al final de una línea. Las opciones de sangría en **Formato** se aplican cuando se da formato automáticamente al código, por ejemplo:

- Cuando pega el código en el archivo mientras está seleccionada la opción **Dar formato automáticamente al pegar**
- Cuando el bloque al que se está dando formato se escribe manualmente

## <a name="see-also"></a>Consulte también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
