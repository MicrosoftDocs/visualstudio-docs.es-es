---
title: Elemento CommandTable | Microsoft Docs
description: CommandTable es el elemento raíz del archivo. Vsct, que define el diseño y el tipo de comandos que proporciona un VSPackage al IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79441880091088cf1d953c8925273e801dc0860d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887359"
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
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

| Atributo | Descripción |
|-----------| - |
| xmlns | Necesario. Espacios de nombres XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = " <http://www.w3.org/2001/XMLSchema> " |
| language | Opcional. El atributo Language se puede usar para especificar el idioma predeterminado de todos los \<Strings> elementos de la tabla de comandos.  Si no se especifica el idioma, se usará el idioma del proceso actual:<br /><br /> Language = "en-US" |

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Extern (elemento)](../extensibility/extern-element.md)|Opcional. Contiene directivas de preprocesador para el compilador.|
|[Elemento include](../extensibility/include-element.md)|Opcional. Contiene las rutas de acceso a los archivos que se van a incluir en la compilación.|
|[Elemento define](../extensibility/define-element.md)|Opcional. Define un símbolo a partir de su nombre y valor.|
|[Elemento Commands](../extensibility/commands-element.md)|Opcional. Elemento primario que define todos los comandos para el VSPackage que contiene todos los demás elementos.|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Opcional. Define dónde se colocarán los comandos en la barra de comandos.|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad estática de los comandos y las barras de herramientas.|
|[KeyBindings (elemento)](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si las hay, para los comandos.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Opcional. Permite que un VSPackage implemente opcionalmente su propia versión de funcionalidad admitida originalmente por otros VSPackages.|
|[Elemento Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Opcional. Contiene datos de símbolos (GUID, identificadores, etc.) para el compilador.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|None||

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
