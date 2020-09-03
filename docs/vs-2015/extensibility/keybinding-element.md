---
title: Elemento KeyBinding | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180329"
---
# <a name="keybinding-element"></a>KeyBinding (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento KeyBinding especifica los métodos abreviados de teclado para los comandos.  
  
 Los comandos pueden tener asociados ambos enlaces de clave única y doble. Un ejemplo de un enlace de clave único es CTRL + S para el comando **Save** . Los enlaces de doble clave requieren dos combinaciones de teclas sucesivas para desencadenar un comando. Un ejemplo de un enlace de doble tecla es CTRL + K, CTRL + K para establecer un marcador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Necesario.|  
|id|Necesario.|  
|editor|Necesario. El GUID del editor indica el contexto de edición para el que este método abreviado de teclado estará activo. El valor de ámbito de enlace global es "guidVSStd97".|  
|key1|Necesario. Entre los valores válidos se incluyen todos los typable alfanuméricos y los valores hexadecimales de dos dígitos precedidos de 0x y VK_constants.|  
|mod1|Opcional. Cualquier combinación de CTRL, ALT y Mayús separadas por espacio.|  
|key2|Opcional. Entre los valores válidos se incluyen todos los typable alfanuméricos y los valores hexadecimales de dos dígitos precedidos de 0x y VK_constants.|  
|mod2|Opcional. Cualquier combinación de CTRL, ALT y Mayús separadas por espacio.|  
|emulator|Opcional.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Parent||  
|Anotación||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[KeyBindings (Elemento)](../extensibility/keybindings-element.md)|Agrupa los elementos KeyBinding y otras agrupaciones de enlaces de teclado.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Consulte también  
 [KeyBindings (elemento)](../extensibility/keybindings-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
