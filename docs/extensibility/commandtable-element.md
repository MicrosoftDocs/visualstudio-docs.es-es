---
title: CommandTable (elemento) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c2adca249ba245825f9b664b46e1b4674d0ea50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879914"
---
# <a name="commandtable-element"></a>CommandTable (elemento)
CommandTable es el elemento raíz de la *.vsct* archivo. Este es el archivo que define el diseño real y el tipo de los comandos que un paquete VSPackage proporciona al IDE. Los comandos pueden incluir elementos de menú, barras de herramientas, menús y cuadros combinados. Para obtener más información, consulte [archivos de tabla (.vsct) de comandos de Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
| xmlns | Requerido. Espacios de nombres XML:<br /><br /> xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns: xs = "<http://www.w3.org/2001/XMLSchema>" |
| lenguaje | Opcional. El atributo language puede utilizarse para especificar el idioma predeterminado de todos los \<cadenas > elementos en la tabla de comandos.  Si no se especifica el idioma, se usará el idioma del proceso actual:<br /><br /> Language = "en-us" |
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Extern (elemento)](../extensibility/extern-element.md)|Opcional. Contiene las directivas de preprocesador para el compilador.|  
|[Elemento de inclusión](../extensibility/include-element.md)|Opcional. Contiene las rutas de acceso a los archivos que se incluyen en la compilación.|  
|[Definir el elemento](../extensibility/define-element.md)|Opcional. Define un símbolo dado su nombre y valor.|  
|[Elemento Commands](../extensibility/commands-element.md)|Opcional. El elemento primario que define todos los comandos para el VSPackage que contiene todos los demás elementos.|  
|[CommandPlacements (elemento)](../extensibility/commandplacements-element.md)|Opcional. Define donde en la barra de comandos, los comandos se va a colocar.|  
|[VisibilityConstraints (elemento)](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad de los comandos y las barras de herramientas estática.|  
|[KeyBindings (elemento)](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si existe, para los comandos.|  
|[UsedCommands (elemento)](../extensibility/usedcommands-element.md)|Opcional. Permite que un paquete VSPackage opcionalmente, puede implementar su propia versión de funcionalidad compatible originalmente con otros VSPackages.|  
|[Symbols (elemento)](https://www.microsoft.com/download/details.aspx?id=55984)|Opcional. Contiene los datos de símbolos--GUID, identificadores y así sucesivamente, para que el compilador.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguna||  
  
## <a name="see-also"></a>Vea también  
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)