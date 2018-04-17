---
title: Elemento de enlaces de teclado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91a5fd99216e712e567d4543f3f29dc2b6b21aa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="keybindings-element"></a>Elemento de enlaces de teclado
Los elementos de un KeyBinding de grupos de elemento de enlaces de teclado y otros grupos de enlaces de teclado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[KeyBinding (Elemento)](../extensibility/keybinding-element.md)|Especifica los métodos abreviados de teclado para los comandos.|  
|[Enlaces de teclado](../extensibility/keybindings-element.md)|Los elementos de un KeyBinding de grupos y otras agrupaciones de enlaces de teclado.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elemento KeyBinding](../extensibility/keybinding-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)