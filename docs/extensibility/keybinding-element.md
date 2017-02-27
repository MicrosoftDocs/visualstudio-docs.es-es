---
title: "Elemento KeyBinding | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, enlaces de teclado"
  - "Elemento KeyBinding (esquema VSCT XML)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Elemento KeyBinding
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento KeyBinding especifica los métodos abreviados de teclado para los comandos.  
  
 Comandos pueden tener uno o dos enlaces de teclado asociados a ellos. Un ejemplo de una combinación de teclas única es CTRL \+ S para la **Guardar** comando. Los enlaces de teclado duales requieren dos combinaciones de teclas sucesivas para desencadenar un comando. Un ejemplo de una combinación de teclas dual es CTRL\+K,CTRL\+K para establecer un marcador.  
  
## Sintaxis  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio.|  
|id|Obligatorio.|  
|Editor de|Obligatorio. El editor de GUID indica el contexto de edición que se activará este método abreviado de teclado. El valor de ámbito de enlace global es "guidVSStd97".|  
|Key1|Obligatorio. Los valores válidos incluyen todos los caracteres alfanuméricos clasificable por tipo y también valores hexadecimales de dos dígitos precedidos por 0 x y VK\_constants.|  
|MOD1|Opcional. Cualquier combinación de CTRL, ALT y MAYÚS separados por espacios.|  
|Key2|Opcional. Los valores válidos incluyen todos los caracteres alfanuméricos clasificable por tipo y también valores hexadecimales de dos dígitos precedidos por 0 x y VK\_constants.|  
|MOD2|Opcional. Cualquier combinación de CTRL, ALT y MAYÚS separados por espacios.|  
|emulador|Opcional.|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Elemento primario||  
|Anotación||  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de enlaces de teclado](../extensibility/keybindings-element.md)|Grupos KeyBinding elementos y otras agrupaciones KeyBindings.|  
  
## Ejemplo  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## Vea también  
 [Elemento de enlaces de teclado](../extensibility/keybindings-element.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)