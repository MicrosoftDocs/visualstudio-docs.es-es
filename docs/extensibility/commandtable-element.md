---
title: Elemento CommandTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f577b52ad2a9b1fd66ed9c24fb2737621aa8554c
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557781"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable es el elemento raíz del archivo *. Vsct* . Este es el archivo que define el diseño y el tipo reales de los comandos que proporciona un VSPackage al IDE. Los comandos pueden incluir elementos de menú, menús, barras de herramientas y cuadros combinados. Para obtener más información, vea [archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

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
 En las secciones siguientes se describen atributos, elementos secundarios y elementos primarios.

### <a name="attributes"></a>Atributos

| Atributo | Descripción |
|-----------| - |
| xmlns | Necesario. Espacios de nombres XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = "<http://www.w3.org/2001/XMLSchema>" |
| language | Opcional. El atributo Language se puede usar para especificar el idioma predeterminado de todas las cadenas de \<> elementos de la tabla de comandos.  Si no se especifica el idioma, se usará el idioma del proceso actual:<br /><br /> Language = "en-US" |

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Extern (elemento)](../extensibility/extern-element.md)|Opcional. Contiene directivas de preprocesador para el compilador.|
|[Elemento include](../extensibility/include-element.md)|Opcional. Contiene las rutas de acceso a los archivos que se van a incluir en la compilación.|
|[Elemento define](../extensibility/define-element.md)|Opcional. Define un símbolo a partir de su nombre y valor.|
|[Commands, elemento](../extensibility/commands-element.md)|Opcional. Elemento primario que define todos los comandos para el VSPackage que contiene todos los demás elementos.|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Opcional. Define dónde se colocarán los comandos en la barra de comandos.|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad estática de los comandos y las barras de herramientas.|
|[KeyBindings (elemento)](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si las hay, para los comandos.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Opcional. Permite que un VSPackage implemente opcionalmente su propia versión de funcionalidad admitida originalmente por otros VSPackages.|
|[Elemento Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Opcional. Contiene datos de símbolos (GUID, identificadores, etc.) para el compilador.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|None||

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)