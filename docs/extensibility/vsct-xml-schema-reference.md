---
title: Referencia del esquema XML de VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94197efeadf8cd7148cbc41f3f71df625718bba7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350733"
---
# <a name="vsct-xml-schema-reference"></a>Referencia del esquema XML de VSCT
Proporciona una tabla de elementos de esquema del compilador de tabla de comandos, con el elemento secundario permitido elementos y atributos para cada uno.

 Un archivo de configuración (.vsct) de la tabla de comandos basado en XML define los elementos de comando que un paquete VSPackage proporciona al entorno de desarrollo integrado (IDE). Estos elementos incluyen elementos de menú, barras de herramientas, menús y cuadros combinados.

> [!NOTE]
> El compilador VSCT puede ejecutar un preprocesador en el archivo .vsct. Dado que normalmente es el preprocesador, que puede definir C++ incluye y macros que tienen la misma sintaxis que se usa en los archivos de C++. En el archivo .vsct se proporcionan ejemplos de este archivo que el **nuevo proyecto** asistente crea para un proyecto de VSPackage.

## <a name="optional-elements"></a>Elementos opcionales
 Algunos elementos VSCT son opcionales. Si un `Parent` no se especifica el argumento, Group_Undefined:0 se pueden implícita. Si un `Icon` argumento no se especifica, se implicarse guidOfficeIcon:msotcidNoIcon. Cuando se define una tecla de método abreviado, la emulación, que no se utiliza normalmente, es opcional.

 Se puede incrustar elementos de mapa de bits en tiempo de compilación especificando la ubicación de la franja de mapa de bits en el `href` argumento. La Tira de mapa de bits se copian durante la combinación en lugar de extraídos de los recursos del archivo DLL. Cuando un `href` se proporciona un argumento, el `usedList` argumento se convierte en opcional y se consideran todas las ranuras en la Tira de mapa de bits utilizado.

 Todos los valores GUID y el identificador deben definirse mediante el uso de nombres simbólicos. Estos nombres pueden definirse en archivos de encabezado o en VSCT \<símbolos > secciones. Los nombres simbólicos deben ser locales, incluidos a través de \<Include > elementos, o que se hace referencia por \<Extern > elementos. Un nombre simbólico se importa desde un archivo de encabezado especificado en un \<Extern > elemento si sigue el patrón simple de #define el valor de símbolo. El valor puede ser otro símbolo siempre que ese símbolo se ha definido previamente. Definiciones de GUID deben seguir el formato OLE o C++. Los valores de identificador pueden ser dígitos decimales o hexadecimales dígitos que van precedidos de 0 x, tal como se muestra en las siguientes líneas:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  Se pueden usar los comentarios XML, pero las herramientas de ida y vuelta gráfica de usuario (GUI) de la interfaz podrían descartarlos. El contenido de \<anotación > se garantiza que los elementos se mantiene independientemente del formato.

## <a name="schema-hierarchy"></a>Jerarquía del esquema
 Un archivo .vsct tiene los siguientes elementos principales.

- [CommandTable (elemento)](../extensibility/commandtable-element.md)

- [Extern (elemento)](../extensibility/extern-element.md)

- [Elemento de inclusión](../extensibility/include-element.md)

- [Definir el elemento](../extensibility/define-element.md)

- [Elemento Commands](../extensibility/commands-element.md)

- [CommandPlacements (elemento)](../extensibility/commandplacements-element.md)

- [VisibilityConstraints (elemento)](../extensibility/visibilityconstraints-element.md)

- [KeyBindings (elemento)](../extensibility/keybindings-element.md)

- [UsedCommands (elemento)](../extensibility/usedcommands-element.md)

- [Elemento primario](../extensibility/parent-element.md)

- [Icon (elemento)](../extensibility/icon-element.md)

- [Strings (elemento)](../extensibility/strings-element.md)

- [Command Flag (elemento)](../extensibility/command-flag-element.md)

- [Symbols (elemento)](../extensibility/symbols-element.md)

- [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../extensibility/internals/command-routing-in-vspackages.md)