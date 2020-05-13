---
title: Referencia de esquema XML de VSCT ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697913"
---
# <a name="vsct-xml-schema-reference"></a>Referencia de esquema XML de VSCT
Proporciona una tabla de elementos de esquema del compilador de tablas de comandos, con elementos secundarios y atributos permitidos para cada uno.

 Un archivo de configuración de tabla de comandos basado en XML (.vsct) define los elementos de comando que un VSPackage proporciona al entorno de desarrollo integrado (IDE). Estos elementos incluyen elementos de menú, menús, barras de herramientas y cuadros combinados.

> [!NOTE]
> El compilador VSCT puede ejecutar un preprocesador en el archivo .vsct. Dado que normalmente se trata del preprocesador C++, puede definir incluye y macros que tienen la misma sintaxis que se utiliza en los archivos C++. Ejemplos de esto se proporcionan en el archivo .vsct que el Asistente para **nuevo proyecto** crea para un proyecto de VSPackage.

## <a name="optional-elements"></a>Elementos opcionales
 Algunos elementos VSCT son opcionales. Si `Parent` no se especifica un argumento, Group_Undefined:0 estará implícita. Si `Icon` no se especifica un argumento, se implicará guidOfficeIcon:msotcidNoIcon. Cuando se define una tecla de método abreviado, la emulación, que normalmente no se utiliza, es opcional.

 Los elementos de mapa de bits se pueden incrustar en `href` tiempo de compilación especificando la ubicación de la franja de mapa de bits en el argumento. La franja de mapa de bits se copia durante la combinación en lugar de extraerse de los recursos del archivo DLL. Cuando `href` se proporciona un `usedList` argumento, el argumento se convierte en opcional y se consideran todas las ranuras de la franja de mapa de bits utilizadas.

 Todos los valores GUID e ID deben definirse mediante nombres simbólicos. Estos nombres se pueden definir en \<archivos de encabezado o en símbolos VSCT> secciones. Los nombres simbólicos deben \<ser locales, incluidos \<a través de Incluir> elementos o a los que haga referencia los elementos de> Externo. Un nombre simbólico se importa desde un \<archivo de encabezado especificado en un elemento Extern> si sigue el patrón simple de #define SYMBOL VALUE. El valor puede ser otro símbolo siempre y cuando ese símbolo se haya definido previamente. Las definiciones GUID deben seguir el formato OLE o C++. Los valores de ID pueden ser dígitos decimales o hexadecimales precedidos por 0x, como se muestra en las siguientes líneas:

- N.o 6D484634-E53D-4a2c-ADCB-55145C9362C8

- á 0x6d484634, 0xe53d, 0x4a2c, á 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 á á

  Se pueden utilizar comentarios XML, pero las herramientas de interfaz gráfica de usuario (GUI) de ida y vuelta pueden descartarlos. Se garantiza \<que el contenido de los elementos de anotación> se mantenga independientemente del formato.

## <a name="schema-hierarchy"></a>Jerarquía del esquema
 Un archivo .vsct tiene los siguientes elementos principales.

- [Elemento CommandTable](../extensibility/commandtable-element.md)

- [Elemento Externo](../extensibility/extern-element.md)

- [Incluir elemento](../extensibility/include-element.md)

- [Definir elemento](../extensibility/define-element.md)

- [Elemento Comandos](../extensibility/commands-element.md)

- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)

- [VisibilityConstraints elemento](../extensibility/visibilityconstraints-element.md)

- [Elemento KeyBindings](../extensibility/keybindings-element.md)

- [Elemento UsedCommands](../extensibility/usedcommands-element.md)

- [Elemento primario](../extensibility/parent-element.md)

- [Elemento Icono](../extensibility/icon-element.md)

- [Elemento Strings](../extensibility/strings-element.md)

- [Elemento Command Flag](../extensibility/command-flag-element.md)

- [Elemento Símbolos](../extensibility/symbols-element.md)

- [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agregan elementos de interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
