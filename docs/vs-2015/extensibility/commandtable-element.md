---
title: CommandTable (elemento) | Microsoft Docs
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
ms.openlocfilehash: 22cbe4fc34ae41f89709d5b20f2c1188edcd0de3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685298"
---
# <a name="commandtable-element"></a>CommandTable (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable es el elemento raíz del archivo .vsct. Este es el archivo que define el diseño real y el tipo de los comandos que un paquete VSPackage proporciona al IDE. Los comandos pueden incluir elementos de menú, barras de herramientas, menús y cuadros combinados. Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|   xmlns   |                                   Obligatorio. Espacios de nombres XML:<br /><br /> xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>"                                   |
| lenguaje  | Opcional. El atributo language puede utilizarse para especificar el idioma predeterminado de todos los \<cadenas > elementos en la tabla de comandos.  Si no se especifica el idioma, se usará el idioma del proceso actual:<br /><br /> language="en-us" |
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Extern (Elemento)](../extensibility/extern-element.md)|Opcional. Contiene las directivas de preprocesador para el compilador.|  
|[Include (Elemento)](../extensibility/include-element.md)|Opcional. Contiene las rutas de acceso a los archivos que se incluyen en la compilación.|  
|[Define (Elemento)](../extensibility/define-element.md)|Opcional. Define un símbolo dado su nombre y valor.|  
|[Commands (Elemento)](../extensibility/commands-element.md)|Opcional. El elemento primario que define todos los comandos para el VSPackage que contiene todos los demás elementos.|  
|[CommandPlacements (Elemento)](../extensibility/commandplacements-element.md)|Opcional. Define donde en la barra de comandos, los comandos se va a colocar.|  
|[VisibilityConstraints (Elemento)](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad de los comandos y las barras de herramientas estática.|  
|[KeyBindings (Elemento)](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si existe, para los comandos.|  
|[UsedCommands (Elemento)](../extensibility/usedcommands-element.md)|Opcional. Permite que un paquete VSPackage opcionalmente, puede implementar su propia versión de funcionalidad compatible originalmente con otros VSPackages.|  
|[Symbols (Elemento)](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcional. Contiene los datos de símbolos--GUID, identificadores y así sucesivamente, para que el compilador.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguna||  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
