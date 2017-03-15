---
title: "Referencia del esquema XML de VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Comando tabla Configuración los archivos Visual Studio (VSCT), el esquema XML"
  - "Elementos de esquema XML VSCT"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Referencia del esquema XML de VSCT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Proporciona una tabla de elementos de esquema del compilador de la tabla de comandos, con secundario permitido elementos y atributos para cada uno.  
  
 Un archivo de configuración \(.vsct\) de la tabla de comandos basado en XML define los elementos de comandos que proporciona un VSPackage en el entorno de desarrollo integrado \(IDE\). Estos elementos incluyen elementos de menú, menús, barras de herramientas y cuadros combinados.  
  
> [!NOTE]
>  El compilador VSCT puede ejecutar un preprocesador en el archivo .vsct. Porque se trata normalmente incluye C\+\+ preprocesador, que puede definir y macros que tienen la misma sintaxis que se utiliza en los archivos de C\+\+. Se proporcionan ejemplos de esto en el .vsct de archivo que el **nuevo proyecto** asistente crea un proyecto de VSPackage.  
  
## Elementos opcionales  
 Algunos elementos VSCT son opcionales. Si un `Parent` argumento no se especifica, se le implícito Group\_Undefined:0. Si un `Icon` argumento no se especifica, se le implícito guidOfficeIcon:msotcidNoIcon. Cuando se define una tecla de método abreviado, la emulación, que no se utiliza por lo general, es opcional.  
  
 Se puede incrustar elementos de mapa de bits en tiempo de compilación mediante la especificación de la ubicación de la banda de mapa de bits en el `href` argumento. La banda de mapa de bits se copian durante la combinación en lugar de extraídos de los recursos de la DLL. Cuando un `href` se proporciona un argumento, el `usedList` argumento se convierte en opcional y se consideran todas las ranuras de la franja de mapa de bits utilizado.  
  
 Todos los valores GUID y el ID deben definirse mediante nombres simbólicos. Estos nombres pueden definirse en archivos de encabezado o en secciones VSCT \< símbolos \>. Los nombres simbólicos deben ser locales, incluido a través de los elementos \< Include \>, o que hacen referencia los elementos \< Extern \>. Un nombre simbólico se importa desde un archivo de encabezado especificado en un elemento \< Extern \> Si sigue el modelo simple de \#define el valor de símbolo. El valor puede ser otro símbolo siempre que ese símbolo se ha definido previamente. Definiciones de GUID deben seguir el formato de OLE o C\+\+. Valores de identificador pueden ser dígitos decimales o hexadecimales dígitos que van precedidos de 0 x, como se muestra en las siguientes líneas:  
  
-   {6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0 x 14, 0x5c, 0 x 93, 0x62, 0xc8}}  
  
 Se pueden utilizar comentarios XML, pero podrían descartarlos herramientas de interfaz gráfica de usuario de ida y vuelta. Se garantiza que el contenido de los elementos \< Annotation \> se mantiene independientemente del formato.  
  
## Jerarquía del esquema  
 Un archivo de vsct tiene los siguientes elementos principales.  
  
 [Elemento CommandTable](../extensibility/commandtable-element.md)  
  
 [Elemento extern](../extensibility/extern-element.md)  
  
 [Elemento include](../extensibility/include-element.md)  
  
 [Definir el elemento](../extensibility/define-element.md)  
  
 [Elemento Commands](../extensibility/commands-element.md)  
  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Elemento de enlaces de teclado](../extensibility/keybindings-element.md)  
  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Elemento Parent](../extensibility/parent-element.md)  
  
 [Icon \(elemento\)](../extensibility/icon-element.md)  
  
 [Elemento de cadenas](../extensibility/strings-element.md)  
  
 [Elemento de indicador de comando](../extensibility/command-flag-element.md)  
  
 [Elemento de símbolos](../extensibility/symbols-element.md)  
  
 [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Enrutamiento de comandos en VSPackages](../extensibility/internals/command-routing-in-vspackages.md)