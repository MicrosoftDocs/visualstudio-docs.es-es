---
title: Elemento Strings | Microsoft Docs
description: El elemento Strings contiene un elemento secundario ButtonText y otros elementos secundarios opcionales. Un símbolo de y comercial en la cadena de texto especifica un método abreviado de teclado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a0bd9ad9b8059eb7fd566c1e0c26a938af6d18b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089906"
---
# <a name="strings-element"></a>Strings (Elemento)
El elemento Strings debe contener al menos un elemento secundario **ButtonText** . Todos los demás elementos secundarios son opcionales. Los caracteres XML no válidos, como ' & ' y ' < ', deben codificarse como entidades (' &amp; ' y ' ', etc &lt; .).

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
|language|Opcional. Language = ".".|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|ButtonText|Este campo y los cinco campos de texto siguientes en una definición de comando permiten especificar el texto que aparece en varios menús. De forma predeterminada, el `ButtonText` campo aparece en controladores de menús. El `ButtonText` campo también se convierte en el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` campo no puede estar en blanco ni siquiera si se especifican los demás campos de texto.|
|ToolTipText (|El `ToolTipText` campo especifica el texto que aparece en la información sobre herramientas de un elemento de menú.<br /><br /> Si el `ToolTipText` campo está en blanco, `ButtonText` se usa el campo.|
|MenuText|El `MenuText` campo especifica el texto que se muestra para un comando si está en el menú principal, una barra de herramientas, en un menú contextual o en un submenú. Si el `MenuText` campo está en blanco, el entorno de desarrollo integrado (IDE) utiliza el `ButtonText` campo. El `MenuText` campo también se puede usar para la localización.<br /><br /> En el caso de los menús contextuales, el `MenuText` campo es el nombre que se muestra en la barra de herramientas de los menús contextuales, lo que permite la personalización de los menús contextuales en el IDE. Por lo tanto, debe ser específico en lo que le asigne el nombre al menú contextual. por ejemplo, use "menú contextual de paquete de widget" en lugar de "acceso directo".<br /><br /> Si `MenuText` no se especifica el campo, `ButtonText` se usa el campo.|
|CommandName|El `CommandName` campo especifica el texto que aparece en la categoría teclado de la ficha **comandos** del cuadro de diálogo **personalizar** (disponible al hacer clic en **personalizar** en el menú **herramientas** ).|
|CanonicalName|El `CanonicalName` campo Inglés especifica el nombre del comando en texto en inglés que se puede escribir en la ventana de **comandos** para ejecutar el elemento de menú. El IDE quita cualquier carácter que no sea una letra, dígitos, caracteres de subrayado ni puntos incrustados. Este texto se concatena después en el `ButtonText` campo para definir el comando. Por ejemplo, **nuevo proyecto** en el menú **archivo** se convierte en el comando archivo. NewProject.<br /><br /> Si `CanonicalName` no se especifica el campo Inglés, el IDE usa el `ButtonText` campo y quita todas las letras, dígitos, caracteres de subrayado y puntos incrustados. Por ejemplo, el texto del botón "&definir comandos..." se convierte en DefineCommands, donde se quitan la y comercial, el espacio y los puntos suspensivos.<br /><br /> Si `TextChanges` se especifica la marca y se cambia el texto del comando, el comando correspondiente reconocido por la ventana de **comandos** no cambia; sigue siendo la forma canónica de los campos originales `ButtonText` o en Inglés `CanonicalName` .|
|LocCanonicalName|El `LocCanonicalName` campo se comporta de forma idéntica al campo Inglés, `CanonicalName` pero permite especificar el texto de comando traducido. Se pueden especificar ambos campos canónicos. Dado que el IDE simplemente analiza el texto escrito en la ventana de **comandos** y lo asocia con un comando, se pueden asociar al mismo comando el texto en inglés y el que no está en inglés.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Button (Elemento)](../extensibility/button-element.md)|Define un elemento con el que el usuario puede interactuar.|
|[Menu (Elemento)](../extensibility/menu-element.md)|Define un elemento de menú único.|
|[Combo (Elemento)](../extensibility/combo-element.md)|Define comandos que aparecen en un cuadro combinado.|

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
