---
title: Opciones, editor de texto, extensión de archivo
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.File_Extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13c79a4cae482990369fc8218bf0b7226ab05942
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919056"
---
# <a name="options-text-editor-file-extension"></a>Opciones, editor de texto, extensión de archivo

Este cuadro de diálogo Opciones le permite especificar cómo se controlarán todos los archivos con determinadas extensiones de archivo mediante el Entorno de desarrollo integrado (IDE) de Visual Studio. Para cada **extensión** que especifique, puede seleccionar un editor asociado. Esto le permite elegir el diseñador o el editor del IDE en el que se abrirán los documentos de un tipo determinado. Para mostrar estas opciones, pulse **Opciones** del menú **Herramientas**, expanda el nodo **Editor de texto** y seleccione **Extensión de archivo**.

Cuando selecciona una opción "con codificación", se mostrará un cuadro de diálogo siempre que abra un documento de ese tipo que le permite seleccionar un esquema de codificación para ese documento. Esto puede resultar útil si está preparando versiones de sus documentos de proyecto para usarlos en diferentes plataformas o en diferentes idiomas de destino.

## <a name="uielement-list"></a>Lista de UIElement

**Extensión**

Escriba la extensión de archivo cuyo editor asociado en el IDE quiere definir.

**Editor**

Seleccione el diseñador o el editor del IDE en el que se abrirán los documentos con esta extensión de archivo. Cuando selecciona una opción "con codificación", se muestra un cuadro de diálogo, siempre que abra un documento que le permita seleccionar un esquema de codificación.

**Add**

Agrega una entrada que incluye la **extensión** y el **editor asociado** especificados a la lista de extensiones.

**Remove**

Elimina la entrada seleccionada de la lista de extensiones.

**Lista de extensiones**

Muestra todas las extensiones para las que se ha especificado un editor asociado.

**Asignar archivos sin extensión**

Seleccione esta opción si quiere especificar cómo se controlarán los archivos sin una extensión mediante el IDE.

**Opciones de archivos sin extensión**

Proporciona la misma lista que el **Editor**. Seleccione el diseñador o el editor del IDE en el que se abrirán los documentos sin extensiones de archivo.

## <a name="see-also"></a>Vea también

- [Cómo: Administrar los modos del editor](../../ide/how-to-manage-editor-modes.md)