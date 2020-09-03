---
title: Elemento CommandTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477046"
---
# <a name="commandtable-element"></a>CommandTable (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable es el elemento raíz del archivo. Vsct. Este es el archivo que define el diseño y el tipo reales de los comandos que proporciona un VSPackage al IDE. Los comandos pueden incluir elementos de menú, menús, barras de herramientas y cuadros combinados. Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
  
| Atributo |                                                                                                                   Descripción                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Necesario. Espacios de nombres XML:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| language  | Opcional. El atributo Language se puede usar para especificar el idioma predeterminado de todos los \<Strings> elementos de la tabla de comandos.  Si no se especifica el idioma, se usará el idioma del proceso actual:<br /><br /> Language = "en-US" |
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Extern (Elemento)](../extensibility/extern-element.md)|Opcional. Contiene directivas de preprocesador para el compilador.|  
|[Elemento include](../extensibility/include-element.md)|Opcional. Contiene las rutas de acceso a los archivos que se van a incluir en la compilación.|  
|[Define (Elemento)](../extensibility/define-element.md)|Opcional. Define un símbolo a partir de su nombre y valor.|  
|[Commands, elemento](../extensibility/commands-element.md)|Opcional. Elemento primario que define todos los comandos para el VSPackage que contiene todos los demás elementos.|  
|[CommandPlacements (Elemento)](../extensibility/commandplacements-element.md)|Opcional. Define dónde se colocarán los comandos en la barra de comandos.|  
|[VisibilityConstraints (Elemento)](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad estática de los comandos y las barras de herramientas.|  
|[KeyBindings (Elemento)](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si las hay, para los comandos.|  
|[UsedCommands (Elemento)](../extensibility/usedcommands-element.md)|Opcional. Permite que un VSPackage implemente opcionalmente su propia versión de funcionalidad admitida originalmente por otros VSPackages.|  
|[Symbols (Elemento)](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcional. Contiene datos de símbolos (GUID, identificadores, etc.) para el compilador.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|None||  
  
## <a name="see-also"></a>Consulte también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
