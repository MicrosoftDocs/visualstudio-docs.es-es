---
title: Referencia del esquema XML de VSCT | Microsoft Docs
description: Los artículos de referencia de esquemas XML de VSCT describen los elementos de esquema de compilador de tabla de comandos, con los atributos y elementos secundarios permitidos para cada uno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cc50d3914f43be0da2f992f1074dc82cf5178ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925743"
---
# <a name="vsct-xml-schema-reference"></a>Referencia del esquema XML de VSCT
Proporciona una tabla de elementos de esquema de compilador de tabla de comandos, con los atributos y elementos secundarios permitidos para cada uno.

 Un archivo de configuración de tabla de comandos basado en XML (. Vsct) define los elementos de comando que un VSPackage proporciona al entorno de desarrollo integrado (IDE). Estos elementos incluyen elementos de menú, menús, barras de herramientas y cuadros combinados.

> [!NOTE]
> El compilador VSCT puede ejecutar un preprocesador en el archivo. VSCT. Dado que suele ser el preprocesador de C++, puede definir inclusiones y macros que tengan la misma sintaxis que se utiliza en los archivos de C++. Se proporcionan ejemplos de esto en el archivo. Vsct que el Asistente para **nuevo proyecto** crea para un proyecto de VSPackage.

## <a name="optional-elements"></a>Elementos opcionales
 Algunos elementos VSCT son opcionales. Si `Parent` no se especifica un argumento, Group_Undefined: 0 estará implícita. Si `Icon` no se especifica un argumento, guidOfficeIcon: msotcidNoIcon estará implícito. Cuando se define una tecla de método abreviado, la emulación, que normalmente no se utiliza, es opcional.

 Los elementos de mapa de bits pueden incrustarse en tiempo de compilación especificando la ubicación de la franja de mapa de bits en el `href` argumento. La franja de mapa de bits se copia durante la combinación en lugar de extraerse de los recursos del archivo DLL. Cuando `href` se proporciona un argumento, el `usedList` argumento se convierte en opcional y se consideran todas las ranuras de la franja de mapa de bits.

 Todos los valores de identificador y GUID deben definirse mediante nombres simbólicos. Estos nombres pueden definirse en archivos de encabezado o en \<Symbols> secciones VSCT. Los nombres simbólicos deben ser locales, incluirse a través de \<Include> elementos o ser referenciados por \<Extern> elementos. Un nombre simbólico se importa de un archivo de encabezado especificado en un \<Extern> elemento si sigue el patrón simple de #define valor de símbolo. El valor puede ser otro símbolo, siempre y cuando ese símbolo se haya definido previamente. Las definiciones de GUID deben seguir el formato de OLE o C++. Los valores de identificador pueden ser dígitos decimales o dígitos hexadecimales precedidos por 0x, tal como se muestra en las líneas siguientes:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}

  Se pueden usar comentarios XML, pero las herramientas de interfaz gráfica de usuario (GUI) de ida y vuelta podrían descartarlos. \<Annotation>Se garantiza que el contenido de los elementos se mantiene independientemente del formato.

## <a name="schema-hierarchy"></a>Jerarquía del esquema
 Un archivo. Vsct tiene los siguientes elementos principales.

- [Elemento CommandTable](../extensibility/commandtable-element.md)

- [Extern (elemento)](../extensibility/extern-element.md)

- [Elemento include](../extensibility/include-element.md)

- [Elemento define](../extensibility/define-element.md)

- [Elemento Commands](../extensibility/commands-element.md)

- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)

- [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [KeyBindings (elemento)](../extensibility/keybindings-element.md)

- [Elemento UsedCommands](../extensibility/usedcommands-element.md)

- [Elemento primario](../extensibility/parent-element.md)

- [Elemento Icon](../extensibility/icon-element.md)

- [Elemento Strings](../extensibility/strings-element.md)

- [Elemento de marca de comando](../extensibility/command-flag-element.md)

- [Elemento Symbols](../extensibility/symbols-element.md)

- [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Vea también
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
