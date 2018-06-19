---
title: Elemento KeyBinding | Documentos de Microsoft
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
ms.openlocfilehash: 226a5913cbaa151689a886dc88986f7de8cc29f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139174"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
El elemento KeyBinding especifica métodos abreviados de teclado para los comandos.  
  
 Comandos pueden tener uno o dos enlaces de clave asociados a ellos. Un ejemplo de un enlace de clave única es CTRL + S para la **guardar** comando. Los enlaces de teclado duales requieren dos combinaciones de teclas sucesivas para desencadenar un comando. Un ejemplo de una combinación de teclas dual es CTRL + K, CTRL + K para establecer un marcador.  
  
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
|editor|Requerido. El editor de GUID indica el contexto de edición para el que se activará este método abreviado de teclado. El valor de ámbito de enlace global es "guidVSStd97".|  
|key1|Requerido. Los valores válidos son clasificable por tipo todos los caracteres alfanuméricos y también valores hexadecimales de dos dígitos precedidos por 0 x y [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD1|Opcional. Cualquier combinación de teclas CTRL, ALT y MAYÚS separados por espacios.|  
|key2|Opcional. Los valores válidos son clasificable por tipo todos los caracteres alfanuméricos y también valores hexadecimales de dos dígitos precedidos por 0 x y [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD2|Opcional. Cualquier combinación de teclas CTRL, ALT y MAYÚS separados por espacios.|  
|emulador|Opcional.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario||  
|Anotación||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[KeyBindings (Elemento)](../extensibility/keybindings-element.md)|Los elementos de un KeyBinding de grupos y otras agrupaciones de enlaces de teclado.|  
  
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
 [Elemento de enlaces de teclado](../extensibility/keybindings-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
