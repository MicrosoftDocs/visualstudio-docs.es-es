---
title: Elemento de enlace de teclado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb8e0dca8293d5d5e853dde19e0c411cfd3e4e63
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495302"
---
# <a name="keybinding-element"></a>KeyBinding (elemento)
El elemento de enlace de teclado especifica métodos abreviados de teclado para los comandos.  
  
 Los comandos pueden tener uno o dos enlaces de teclado asociados con ellos. Es un ejemplo de un enlace de clave único **Ctrl**+**S** para el **guardar** comando. Los enlaces de teclado duales requieren dos combinaciones de teclas sucesivas para desencadenar un comando. Es un ejemplo de un enlace dual clave **Ctrl * +** K **,** Ctrl**+** K ** para establecer un marcador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Requerido.|  
|id|Requerido.|  
|editor|Requerido. El GUID de editor indica el contexto de edición para el que este método abreviado de teclado estará activa. El valor de ámbito de enlace global es "guidVSStd97".|  
|key1|Requerido. Los valores válidos incluyen caracteres alfanuméricos clasificable todo por tipo y también valores hexadecimales de dos dígitos precedidos por 0 x y [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|MOD1|Opcional. Cualquier combinación de **Ctrl**, **Alt**, y **MAYÚS** separados por espacios.|  
|key2|Opcional. Los valores válidos incluyen caracteres alfanuméricos clasificable todo por tipo y también valores hexadecimales de dos dígitos precedidos por 0 x y [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|MOD2|Opcional. Cualquier combinación de **Ctrl**, **Alt**, y **MAYÚS** separados por espacios.|  
|Emulador|Opcional.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario||  
|Anotación||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[KeyBindings (elemento)](../extensibility/keybindings-element.md)|Agrupa los elementos de enlace de teclado y otras agrupaciones de los enlaces de teclado.|  
  
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
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
