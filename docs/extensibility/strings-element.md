---
title: Elemento Strings | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719445"
---
# <a name="strings-element"></a>Strings (Elemento)
El elemento Strings debe contener al menos un elemento secundario **ButtonText** . Todos los demás elementos secundarios son opcionales. Los caracteres XML no válidos, como ' & ' y ' < ', deben codificarse como entidades (' &amp; ' y ' &lt; ', etc.).

 Una y comercial en la cadena de texto especifica el método abreviado de teclado para el comando.

## <a name="syntax"></a>Sintaxis

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|lenguaje|Opcional. Language = ".".|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|ButtonText|Este campo y los cinco campos de texto siguientes en una definición de comando permiten especificar el texto que aparece en varios menús. De forma predeterminada, el campo `ButtonText` aparece en controladores de menús. El campo `ButtonText` también se convierte en el valor predeterminado si los demás campos de texto están en blanco. El campo `ButtonText` no puede estar en blanco ni siquiera si se especifican los demás campos de texto.|
|ToolTipText (|El campo `ToolTipText` especifica el texto que aparece en la información sobre herramientas de un elemento de menú.<br /><br /> Si el campo `ToolTipText` está en blanco, se usa el campo `ButtonText`.|
|MenuText|El campo `MenuText` especifica el texto que se muestra para un comando si está en el menú principal, una barra de herramientas, en un menú contextual o en un submenú. Si el campo `MenuText` está en blanco, el entorno de desarrollo integrado (IDE) utiliza el campo `ButtonText`. También se puede usar el campo `MenuText` para la localización.<br /><br /> En el caso de los menús contextuales, el campo `MenuText` es el nombre que se muestra en la barra de herramientas de los menús contextuales, lo que permite la personalización de los menús contextuales en el IDE. Por lo tanto, debe ser específico en lo que le asigne el nombre al menú contextual. por ejemplo, use "menú contextual de paquete de widget" en lugar de "acceso directo".<br /><br /> Si no se especifica el campo `MenuText`, se usa el campo `ButtonText`.|
|CommandName|El campo `CommandName` especifica el texto que aparece en la categoría teclado de la ficha **comandos** del cuadro de diálogo **personalizar** (disponible al hacer clic en **personalizar** en el menú **herramientas** ).|
|CanonicalName|El campo `CanonicalName` en inglés especifica el nombre del comando en texto en inglés que se puede escribir en la ventana de **comandos** para ejecutar el elemento de menú. El IDE quita cualquier carácter que no sea una letra, dígitos, caracteres de subrayado ni puntos incrustados. Este texto se concatena después en el campo `ButtonText` para definir el comando. Por ejemplo, **nuevo proyecto** en el menú **archivo** se convierte en el comando archivo. NewProject.<br /><br /> Si no se especifica el campo `CanonicalName` en inglés, el IDE usa el campo `ButtonText` y elimina todas las letras, dígitos, caracteres de subrayado y puntos incrustados. Por ejemplo, el texto del botón "& definir comandos..." se convierte en DefineCommands, donde se quitan la y comercial, el espacio y los puntos suspensivos.<br /><br /> Si se especifica la marca de `TextChanges` y se cambia el texto del comando, el comando correspondiente reconocido por la ventana de **comandos** no cambia. sigue siendo la forma canónica de los campos de `CanonicalName` originales `ButtonText` o en inglés.|
|LocCanonicalName|El campo `LocCanonicalName` se comporta igual que el campo `CanonicalName` en inglés, pero permite especificar el texto de comando localizado. Se pueden especificar ambos campos canónicos. Dado que el IDE simplemente analiza el texto escrito en la ventana de **comandos** y lo asocia con un comando, se pueden asociar al mismo comando el texto en inglés y el que no está en inglés.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Button (Elemento)](../extensibility/button-element.md)|Define un elemento con el que el usuario puede interactuar.|
|[Menu (Elemento)](../extensibility/menu-element.md)|Define un elemento de menú único.|
|[Combo (Elemento)](../extensibility/combo-element.md)|Define comandos que aparecen en un cuadro combinado.|

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)