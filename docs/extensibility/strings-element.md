---
title: Cadenas de elemento | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de2ed5d9c757d9082cd06c2aae5a8e51b0865714
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699410"
---
# <a name="strings-element"></a>Strings (Elemento)
El elemento de cadenas debe contener al menos un **ButtonText** elemento secundario. Todos los demás elementos secundarios son opcionales. Los caracteres XML no válido, como '&' y ' <' deben codificarse como entidades ('&amp;'y'&lt;' y así sucesivamente).

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
|ButtonText|Este campo y los cinco campos de texto siguiente en una definición de comando le permiten especificar el texto que aparece en varios menús. De forma predeterminada, el `ButtonText` campo aparece en los controladores de menú. El `ButtonText` campo también se convierte el valor predeterminado en si los demás campos de texto están en blanco. El `ButtonText` campo no puede estar en blanco, incluso si se especifican los demás campos de texto.|
|ToolTipText|El `ToolTipText` campo especifica el texto que aparece en la información sobre herramientas para un elemento de menú.<br /><br /> Si el `ToolTipText` campo está en blanco, el `ButtonText` se usa el campo.|
|MenuText|El `MenuText` campo especifica el texto que se muestra para un comando si se encuentra en el menú principal, una barra de herramientas, en un menú contextual o en un submenú. Si el `MenuText` campo está en blanco, el entorno de desarrollo integrado (IDE) utiliza el `ButtonText` campo. El `MenuText` campo también se puede utilizar para la localización.<br /><br /> Para los menús contextuales, la `MenuText` campo es el nombre que se muestra en la barra de herramientas de los menús contextuales, lo que permite la personalización de menús contextuales en el IDE. Por lo tanto, ser específico en qué nombre de su menú contextual; Por ejemplo, use "Widget paquete acceso directo" en lugar de "Acceso directo".<br /><br /> Si el `MenuText` campo no se especifica, el `ButtonText` se usa el campo.|
|CommandName|El `CommandName` campo especifica el texto que aparece en la categoría de teclado en el **comandos** pestaña en el **personalizar** cuadro de diálogo (disponible al hacer clic en **personalizar**en el **herramientas** menú).|
|CanonicalName|El inglés `CanonicalName` campo especifica el nombre del comando de texto en inglés que se puede escribir en el **comando** ventana para ejecutar el elemento de menú. El IDE elimina todos los caracteres que no son letras, números, caracteres de subrayado o puntos incrustados. Este texto, a continuación, se concatena la `ButtonText` campo para definir el comando. Por ejemplo, **nuevo proyecto** en el **archivo** menú se convierte en el comando, File.NewProject.<br /><br /> Si el inglés `CanonicalName` campo no se especifica, el IDE usa la `ButtonText` campo y estropea todo excepto letras, dígitos, caracteres de subrayado y puntos incrustados. Por ejemplo, el texto del botón "& definir comandos..." se convierte en DefineCommands, donde se quitan la y comercial, el espacio y los puntos suspensivos.<br /><br /> Si el `TextChanges` se especifica la marca y se cambia el texto del comando, el comando correspondiente que reconoce el **comando** ventana no cambia, sigue siendo la forma canónica del original `ButtonText` o inglés `CanonicalName` campos.|
|LocCanonicalName|El `LocCanonicalName` campo tiene un comportamiento idéntico para el inglés `CanonicalName` campo pero permite el texto del comando localizado que se especifique. Se pueden especificar ambos campos canónicos. Dado que el IDE solo analiza el texto escrito en el **comando** ventana y la asocia con un comando, tanto en inglés como texto no inglesas puede estar asociado con el mismo comando.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Button (Elemento)](../extensibility/button-element.md)|Define un elemento que el usuario puede interactuar con.|
|[Menu (Elemento)](../extensibility/menu-element.md)|Define un elemento de menú único.|
|[Combo (Elemento)](../extensibility/combo-element.md)|Define los comandos que aparecen en un cuadro combinado.|

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)