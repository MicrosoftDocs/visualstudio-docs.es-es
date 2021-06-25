---
title: Elemento Strings | Microsoft Docs
description: El elemento Strings contiene un elemento secundario ButtonText y otros elementos secundarios opcionales. Una yerba en la cadena de texto especifica un método abreviado de teclado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899412"
---
# <a name="strings-element"></a>Strings (Elemento)
El elemento Strings debe contener al menos un **elemento secundario ButtonText.** Todos los demás elementos secundarios son opcionales. Los caracteres XML no válidos, como "&" y "<", se deben codificar como entidades (' ' y &amp; ' ' y así &lt; sucesivamente).

 Una yerba en la cadena de texto especifica el método abreviado de teclado para el comando.

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
|language|Opcional. Language=".".|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|ButtonText|Este campo y los cinco campos de texto siguientes de una definición de comando permiten especificar el texto que aparece en varios menús. De forma predeterminada, el `ButtonText` campo aparece en los controladores de menú. El `ButtonText` campo también se convierte en el valor predeterminado si los demás campos de texto están en blanco. El campo no puede estar en blanco aunque se especifiquen `ButtonText` los demás campos de texto.|
|ToolTipText|El `ToolTipText` campo especifica el texto que aparece en la información sobre herramientas de un elemento de menú.<br /><br /> Si el `ToolTipText` campo está en blanco, se usa el `ButtonText` campo .|
|MenuText|El campo especifica el texto que se muestra para un comando si está en el menú principal, en una barra de herramientas, en un menú contextual o en `MenuText` un submenú. Si el `MenuText` campo está en blanco, el entorno de desarrollo integrado (IDE) usa el `ButtonText` campo . El `MenuText` campo también se puede usar para la localización.<br /><br /> Para los menús contextuales, el campo es el nombre que se muestra en la barra de herramientas Menús contextuales, lo que permite personalizar los menús contextuales `MenuText` en el IDE. Por lo tanto, sea específico en lo que asigne un nombre al menú contextual; por ejemplo, use "Menú contextual del paquete de widget" en lugar de "Acceso directo".<br /><br /> Si no `MenuText` se especifica el campo, se usa el `ButtonText` campo .|
|CommandName|El campo especifica el texto que aparece en la categoría de teclado en la pestaña Comandos del cuadro de diálogo Personalizar (disponible haciendo clic en Personalizar en `CommandName` el **menú** Herramientas).   |
|CanonicalName|El campo Inglés especifica el nombre del comando en texto en inglés que se puede especificar en la ventana `CanonicalName` Comando para ejecutar el elemento de menú.  El IDE elimina los caracteres que no son letras, dígitos, caracteres de subrayado o puntos incrustados. A continuación, este texto se concatena al `ButtonText` campo para definir el comando. Por ejemplo, **Nuevo proyecto en** el **menú** Archivo se convierte en el comando File.NewProject.<br /><br /> Si no se especifica el campo inglés, el IDE usa el campo y elimina todos, excepto las letras, los dígitos, los caracteres de subrayado y los puntos `CanonicalName` `ButtonText` incrustados. Por ejemplo, el texto del botón "&Definir comandos...". se convierte en DefineCommands, donde se quitan las yerras, el espacio y los puntos suspensivos.<br /><br /> Si se especifica la marca y se cambia el texto del comando, el comando correspondiente reconocido por la ventana Comando no cambia; sigue siendo la forma canónica de los campos originales o `TextChanges`  `ButtonText` `CanonicalName` inglés.|
|LocCanonicalName|El campo se comporta de forma idéntica al campo inglés, pero permite especificar texto de `LocCanonicalName` `CanonicalName` comando localizado. Se pueden especificar ambos campos canónicos. Dado que el IDE solo analiza  el texto especificado en la ventana Comando y lo asocia a un comando, el texto en inglés y el texto que no sea inglés se puede asociar con el mismo comando.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Button (Elemento)](../extensibility/button-element.md)|Define un elemento con el que el usuario puede interactuar.|
|[Menu (Elemento)](../extensibility/menu-element.md)|Define un único elemento de menú.|
|[Combo (Elemento)](../extensibility/combo-element.md)|Define los comandos que aparecen en un cuadro combinado.|

## <a name="see-also"></a>Consulta también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
