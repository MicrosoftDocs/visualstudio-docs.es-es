---
title: Elemento CommandTable (CommandTable Element) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739647"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable es el elemento raíz del archivo *.vsct.* Este es el archivo que define el diseño real y el tipo de los comandos que un VSPackage proporciona al IDE. Los comandos pueden incluir elementos de menú, menús, barras de herramientas y cuadros combinados. Para obtener más información, vea Archivos de tabla de [comandos de Visual Studio (.vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| xmlns | Necesario. Espacios de nombres XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs"<http://www.w3.org/2001/XMLSchema>" |
| language | Opcional. El atributo language se puede utilizar para \<especificar el idioma predeterminado de todas las cadenas> elementos de la tabla de comandos.  Si no se especifica el idioma, se utilizará el idioma del proceso actual:<br /><br /> "en-nosotros" |

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Externo](../extensibility/extern-element.md)|Opcional. Contiene directivas de preprocesador para el compilador.|
|[Incluir elemento](../extensibility/include-element.md)|Opcional. Contiene rutas de acceso a los archivos que se van a incluir en la compilación.|
|[Definir elemento](../extensibility/define-element.md)|Opcional. Define un símbolo dado su nombre y valor.|
|[Elemento Comandos](../extensibility/commands-element.md)|Opcional. El elemento primario que define todos los comandos para el VSPackage que contiene todos los demás elementos.|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Opcional. Define dónde se van a colocar los comandos en la barra de comandos.|
|[VisibilityConstraints elemento](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad estática de comandos y barras de herramientas.|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si las hay, para los comandos.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Opcional. Permite que un VSPackage implemente opcionalmente su propia versión de funcionalidad originalmente compatible con otros VSPackages.|
|[Elemento Símbolos](https://www.microsoft.com/download/details.aspx?id=55984)|Opcional. Contiene los datos de símbolos -- GUID, IDs, etc.- para el compilador.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|None||

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
