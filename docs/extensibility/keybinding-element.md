---
title: Elemento KeyBinding | Microsoft Docs
description: El elemento KeyBinding especifica métodos abreviados de teclado para los comandos. Los comandos pueden tener enlaces de clave únicos y duales asociados a ellos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6afd0a9658f088b66f2c18c632ffcd7b9a09f555
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898866"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
El elemento KeyBinding especifica métodos abreviados de teclado para los comandos.

 Los comandos pueden tener enlaces de clave únicos y duales asociados a ellos. Un ejemplo de un enlace de teclado único es **Ctrl** + **S** para el **comando** Guardar. Los enlaces de clave dual requieren dos combinaciones de claves sucesivas para desencadenar un comando. Un ejemplo de un enlace de teclado dual es <strong>Ctrl *+</strong> K <strong>,</strong>Ctrl <strong>+</strong> K** para establecer un marcador.

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
|editor|Necesario. El GUID del editor indica el contexto de edición para el que este método abreviado de teclado estará activo. El valor del ámbito de enlace global es "guidVSStd97".|
|key1|Necesario. Los valores válidos incluyen todos los caracteres alfanuméricos tipográficos y también los valores hexadecimales de dos dígitos precedidos de 0x [y VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Opcional. Cualquier combinación de **Ctrl,** **Alt** y **Mayús separadas** por espacio.|
|key2|Opcional. Los valores válidos incluyen todos los caracteres alfanuméricos tipográficos y también los valores hexadecimales de dos dígitos precedidos de 0x [y VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Opcional. Cualquier combinación de **Ctrl,** **Alt** y **Mayús separadas** por espacio.|
|emulator|Opcional.|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent||
|Anotación||

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Agrupa elementos KeyBinding y otras agrupaciones de KeyBindings.|

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
- [Elemento KeyBindings](../extensibility/keybindings-element.md)
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
