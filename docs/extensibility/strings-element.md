---
title: Elemento de las cadenas de la cadena de la cadena de Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699729"
---
# <a name="strings-element"></a>Strings (Elemento)
El elemento Strings debe contener al menos un elemento secundario **ButtonText.** Todos los demás elementos secundarios son opcionales. Los caracteres XML no válidos como '&' y '<' deben codificarse como entidades ('&amp;' y '&lt;' ' etc.).

 Una y unana en la cadena de texto especifica el método abreviado de teclado para el comando.

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
|language|Opcional. Idioma".".|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|ButtonText|Este campo y los cinco campos de texto siguientes en una definición de comando le permiten especificar el texto que aparece en varios menús. De forma `ButtonText` predeterminada, el campo aparece en los controladores de menú. El `ButtonText` campo también se convierte en el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` campo no puede estar en blanco aunque se especifiquen los demás campos de texto.|
|ToolTipText|El `ToolTipText` campo especifica el texto que aparece en la información sobre herramientas de un elemento de menú.<br /><br /> Si `ToolTipText` el campo está `ButtonText` en blanco, se utiliza el campo.|
|MenuText|El `MenuText` campo especifica el texto que se muestra para un comando si está en el menú principal, una barra de herramientas, en un menú contextual o en un submenú. Si `MenuText` el campo está en blanco, el entorno `ButtonText` de desarrollo integrado (IDE) utiliza el campo. El `MenuText` campo también se puede utilizar para la localización.<br /><br /> Para los menús contextuales, el `MenuText` campo es el nombre que se muestra en la barra de herramientas Menús contextuales, que permite la personalización de los menús contextuales en el IDE. Por lo tanto, sea específico en lo que usted nombra el menú contextual; por ejemplo, utilice "Menú de acceso directo del paquete de widgets" en lugar de "Acceso directo".<br /><br /> Si `MenuText` no se especifica el `ButtonText` campo, se utiliza el campo.|
|CommandName|El `CommandName` campo especifica el texto que aparece en la categoría de teclado en la ficha **Comandos** del cuadro de diálogo **Personalizar** (disponible haciendo clic en **Personalizar** en el menú **Herramientas).**|
|CanonicalName|El `CanonicalName` campo Inglés especifica el nombre del comando en texto en inglés que se puede introducir en la ventana **Comando** para ejecutar el elemento de menú. El IDE elimina los caracteres que no son letras, dígitos, guiones bajos o períodos incrustados. A continuación, este texto `ButtonText` se concatena al campo para definir el comando. Por ejemplo, **Nuevo proyecto** en **el** archivo menú se convierte en el comando, File.NewProject.<br /><br /> Si no `CanonicalName` se especifica el campo Inglés, el IDE usa el `ButtonText` campo y elimina todas las letras, dígitos, guiones bajos y períodos incrustados. Por ejemplo, el texto del botón "&Definir comandos..." se convierte en DefineCommands, donde se quitan las y anquiersand, el espacio y los puntos suspensivos.<br /><br /> Si `TextChanges` se especifica el indicador y se cambia el texto del comando, el comando correspondiente reconocido por la ventana **Comando** no cambia; sigue siendo la forma `ButtonText` canónica de los campos originales o ingleses. `CanonicalName`|
|LocCanonicalName|El `LocCanonicalName` campo se comporta de `CanonicalName` forma idéntica al campo Inglés, pero permite especificar el texto del comando localizado. Se pueden especificar ambos campos canónicos. Dado que el IDE solo analiza el texto introducido en la ventana **Comando** y lo asocia con un comando, el texto en inglés y el no inglés se pueden asociar al mismo comando.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Button (Elemento)](../extensibility/button-element.md)|Define un elemento con el que el usuario puede interactuar.|
|[Menu (Elemento)](../extensibility/menu-element.md)|Define un único elemento de menú.|
|[Combo (Elemento)](../extensibility/combo-element.md)|Define los comandos que aparecen en un cuadro combinado.|

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
