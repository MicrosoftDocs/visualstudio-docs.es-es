---
title: Referencia del esquema XML de VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2129dcb4f8be717ab37c5e220b2d4b65f3b16698
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840836"
---
# <a name="vsct-xml-schema-reference"></a>Referencia del esquema XML de VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proporciona una tabla de elementos de esquema del compilador de tabla de comandos, con el elemento secundario permitido elementos y atributos para cada uno.  
  
 Un archivo de configuración (.vsct) de la tabla de comandos basado en XML define los elementos de comando que un paquete VSPackage proporciona al entorno de desarrollo integrado (IDE). Estos elementos incluyen elementos de menú, barras de herramientas, menús y cuadros combinados.  
  
> [!NOTE]
>  El compilador VSCT puede ejecutar un preprocesador en el archivo .vsct. Dado que normalmente es el preprocesador, que puede definir C++ incluye y macros que tienen la misma sintaxis que se usa en los archivos de C++. En el archivo .vsct se proporcionan ejemplos de este archivo que el **nuevo proyecto** asistente crea para un proyecto de VSPackage.  
  
## <a name="optional-elements"></a>Elementos opcionales  
 Algunos elementos VSCT son opcionales. Si un `Parent` argumento no se especifica, se implicarse Group_Undefined:0. Si un `Icon` argumento no se especifica, se implicarse guidOfficeIcon:msotcidNoIcon. Cuando se define una tecla de método abreviado, la emulación, que no se utiliza normalmente, es opcional.  
  
 Se puede incrustar elementos de mapa de bits en tiempo de compilación especificando la ubicación de la franja de mapa de bits en el `href` argumento. La Tira de mapa de bits se copian durante la combinación en lugar de extraídos de los recursos del archivo DLL. Cuando un `href` se proporciona un argumento, el `usedList` argumento se convierte en opcional y se consideran todas las ranuras en la Tira de mapa de bits utilizado.  
  
 Todos los valores GUID y el identificador deben definirse mediante el uso de nombres simbólicos. Estos nombres pueden definirse en archivos de encabezado o en VSCT \<símbolos > secciones. Los nombres simbólicos deben ser locales, incluidos a través de \<Include > elementos, o que se hace referencia por \<Extern > elementos. Un nombre simbólico se importa desde un archivo de encabezado especificado en un \<Extern > elemento si sigue el patrón simple de #define el valor de símbolo. El valor puede ser otro símbolo siempre que ese símbolo se ha definido previamente. Definiciones de GUID deben seguir el formato OLE o C++. Los valores de identificador pueden ser dígitos decimales o hexadecimales dígitos que van precedidos de 0 x, tal como se muestra en las siguientes líneas:  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0 x 14, 0x5c, 0 x 93, 0 x 62, 0xc8}}  
  
  Se pueden usar los comentarios XML, pero las herramientas de ida y vuelta gráfica de usuario (GUI) de la interfaz podrían descartarlos. El contenido de \<anotación > se garantiza que los elementos se mantiene independientemente del formato.  
  
## <a name="schema-hierarchy"></a>Jerarquía del esquema  
 Un archivo .vsct tiene los siguientes elementos principales.  
  
 [CommandTable (Elemento)](../extensibility/commandtable-element.md)  
  
 [Extern (Elemento)](../extensibility/extern-element.md)  
  
 [Include (Elemento)](../extensibility/include-element.md)  
  
 [Define (Elemento)](../extensibility/define-element.md)  
  
 [Commands (Elemento)](../extensibility/commands-element.md)  
  
 [CommandPlacements (Elemento)](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints (Elemento)](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings (Elemento)](../extensibility/keybindings-element.md)  
  
 [UsedCommands (Elemento)](../extensibility/usedcommands-element.md)  
  
 [Parent (Elemento)](../extensibility/parent-element.md)  
  
 [Icon (Elemento)](../extensibility/icon-element.md)  
  
 [Strings (Elemento)](../extensibility/strings-element.md)  
  
 [Command Flag (Elemento)](../extensibility/command-flag-element.md)  
  
 [Symbols (Elemento)](../extensibility/symbols-element.md)  
  
 [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Enrutamiento de comandos en VSPackages](../extensibility/internals/command-routing-in-vspackages.md)

