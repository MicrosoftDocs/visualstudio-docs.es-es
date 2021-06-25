---
title: Elemento CommandTable | Microsoft Docs
description: CommandTable es el elemento raíz del archivo .vsct, que define el diseño y el tipo de los comandos que proporciona un VSPackage al IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 55faf4ee8bdc7ec261508fd07f5a573e7a29560f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901856"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable es el elemento raíz del *archivo .vsct.* Este es el archivo que define el diseño real y el tipo de los comandos que proporciona un VSPackage al IDE. Los comandos pueden incluir elementos de menú, menús, barras de herramientas y cuadros combinados. Para obtener más información, [vea Visual Studio archivos de tabla de comandos (.vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="syntax"></a>Sintaxis

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

| Atributo | Descripción |
|-----------| - |
| xmlns | Necesario. Espacios de nombres XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs=" <http://www.w3.org/2001/XMLSchema> " |
| language | Opcional. El atributo language se puede usar para especificar el idioma predeterminado de todos los \<Strings> elementos de la tabla de comandos.  Si no se especifica el idioma, se usará el idioma del proceso actual:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Extern](../extensibility/extern-element.md)|Opcional. Contiene directivas de preprocesador para el compilador.|
|[Elemento Include](../extensibility/include-element.md)|Opcional. Contiene rutas de acceso a los archivos que se incluirán en la compilación.|
|[Definir elemento](../extensibility/define-element.md)|Opcional. Define un símbolo según su nombre y valor.|
|[Elemento Commands](../extensibility/commands-element.md)|Opcional. Elemento primario que define todos los comandos para el VSPackage que contiene todos los demás elementos.|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Opcional. Define dónde se van a colocar los comandos en la barra de comandos.|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad estática de los comandos y las barras de herramientas.|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si las hay, para los comandos.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Opcional. Permite que un VSPackage implemente opcionalmente su propia versión de funcionalidad originalmente compatible con otros VSPackages.|
|[Elemento Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Opcional. Contiene los datos de símbolos (GUID, ID, etc.) del compilador.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno||

## <a name="see-also"></a>Consulta también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
