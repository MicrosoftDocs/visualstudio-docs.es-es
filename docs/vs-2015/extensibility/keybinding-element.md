---
title: Elemento de enlace de teclado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996080"
---
# <a name="keybinding-element"></a>KeyBinding (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento de enlace de teclado especifica métodos abreviados de teclado para los comandos.  
  
 Los comandos pueden tener uno o dos enlaces de teclado asociados con ellos. Un ejemplo de un enlace de clave único es CTRL + S para el **guardar** comando. Los enlaces de teclado duales requieren dos combinaciones de teclas sucesivas para desencadenar un comando. Un ejemplo de una combinación de teclas dual es CTRL + K, CTRL + K para establecer un marcador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Obligatorio.|  
|id|Obligatorio.|  
|editor|Obligatorio. El GUID de editor indica el contexto de edición para el que este método abreviado de teclado estará activa. El valor de ámbito de enlace global es "guidVSStd97".|  
|key1|Obligatorio. Los valores válidos incluyen todos los caracteres alfanuméricos clasificable por tipo y también los valores hexadecimales de dos dígitos precedidos por 0 x y VK_constants.|  
|MOD1|Opcional. Cualquier combinación de CTRL, ALT y MAYÚS separados por espacios.|  
|key2|Opcional. Los valores válidos incluyen todos los caracteres alfanuméricos clasificable por tipo y también los valores hexadecimales de dos dígitos precedidos por 0 x y VK_constants.|  
|MOD2|Opcional. Cualquier combinación de CTRL, ALT y MAYÚS separados por espacios.|  
|Emulador|Opcional.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Primario||  
|Anotación||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[KeyBindings (Elemento)](../extensibility/keybindings-element.md)|Agrupa los elementos de enlace de teclado y otras agrupaciones de los enlaces de teclado.|  
  
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
 [KeyBindings (elemento)](../extensibility/keybindings-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
