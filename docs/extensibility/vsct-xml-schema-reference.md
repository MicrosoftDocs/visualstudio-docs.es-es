---
title: Referencia de esquema XML de VSCT | Microsoft Docs
description: En los artículos de referencia de esquema XML de VSCT se describen los elementos de esquema del compilador de tablas de comandos, con atributos y elementos secundarios permitidos para cada uno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d82cda9c91642b094deea50eda02676f9bb73f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905233"
---
# <a name="vsct-xml-schema-reference"></a>Referencia de esquema XML de VSCT
Proporciona una tabla de elementos de esquema del compilador de tabla de comandos, con atributos y elementos secundarios permitidos para cada uno.

 Un archivo de configuración de tabla de comandos basado en XML (.vsct) define los elementos de comando que un VSPackage proporciona al entorno de desarrollo integrado (IDE). Estos elementos incluyen elementos de menú, menús, barras de herramientas y cuadros combinados.

> [!NOTE]
> El compilador de VSCT puede ejecutar un preprocesador en el archivo .vsct. Dado que suele ser el preprocesador de C++, puede definir las macros includes y que tienen la misma sintaxis que se usa en los archivos de C++. Se proporcionan ejemplos de esto en el  archivo .vsct que el Asistente para nuevo proyecto crea para un proyecto de VSPackage.

## <a name="optional-elements"></a>Elementos opcionales
 Algunos elementos VSCT son opcionales. Si no `Parent` se especifica un argumento, Group_Undefined:0 estará implícito. Si no `Icon` se especifica un argumento, se implicará guidOfficeIcon:msotcidNoIcon. Cuando se define una tecla de método abreviado, la emulación, que normalmente no se usa, es opcional.

 Los elementos de mapa de bits se pueden incrustar en tiempo de compilación especificando la ubicación de la franja de mapa de bits en el `href` argumento . La franja de mapa de bits se copia durante la combinación en lugar de extraerse de los recursos del archivo DLL. Cuando se proporciona un argumento, el argumento se convierte en opcional y se consideran usadas todas las ranuras de `href` la franja de mapa de `usedList` bits.

 Todos los valores guid e id. deben definirse mediante nombres simbólicos. Estos nombres se pueden definir en archivos de encabezado o en secciones \<Symbols> de VSCT. Los nombres simbólicos deben ser locales, incluirse a través \<Include> de elementos o hacer referencia a ellos los elementos \<Extern> . Un nombre simbólico se importa desde un archivo de encabezado especificado en un elemento si sigue el patrón \<Extern> simple de #define SYMBOL VALUE. El valor puede ser otro símbolo siempre que ese símbolo se haya definido previamente. Las definiciones de GUID deben seguir el formato OLE o C++. Los valores de identificador pueden ser dígitos decimales o dígitos hexadecimales precedidos de 0x, como se muestra en las líneas siguientes:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  Se pueden usar comentarios XML, pero las herramientas de interfaz gráfica de usuario (GUI) de ida y vuelta podrían descartarlos. Se garantiza que \<Annotation> el contenido de los elementos se mantenga independientemente del formato.

## <a name="schema-hierarchy"></a>Jerarquía del esquema
 Un archivo .vsct tiene los siguientes elementos principales.

- [Elemento CommandTable](../extensibility/commandtable-element.md)

- [Elemento Extern](../extensibility/extern-element.md)

- [Elemento Include](../extensibility/include-element.md)

- [Definir elemento](../extensibility/define-element.md)

- [Elemento Commands](../extensibility/commands-element.md)

- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)

- [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Elemento KeyBindings](../extensibility/keybindings-element.md)

- [Elemento UsedCommands](../extensibility/usedcommands-element.md)

- [Elemento primario](../extensibility/parent-element.md)

- [Elemento Icon](../extensibility/icon-element.md)

- [Elemento Strings](../extensibility/strings-element.md)

- [Elemento Command Flag](../extensibility/command-flag-element.md)

- [Elemento Symbols](../extensibility/symbols-element.md)

- [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Consulta también
- [Cómo agregan vsPackages elementos de interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
