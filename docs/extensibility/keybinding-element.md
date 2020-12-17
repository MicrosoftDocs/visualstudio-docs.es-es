---
title: Elemento KeyBinding | Microsoft Docs
description: El elemento KeyBinding especifica los métodos abreviados de teclado para los comandos. Los comandos pueden tener asociados ambos enlaces de clave única y doble.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33b2c1638b41afbdae56e0c4374937e7230dfffe
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616122"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
El elemento KeyBinding especifica los métodos abreviados de teclado para los comandos.

 Los comandos pueden tener asociados ambos enlaces de clave única y doble. Un ejemplo de un enlace de clave único es **Ctrl** + **S** para el comando **Save** . Los enlaces de doble clave requieren dos combinaciones de teclas sucesivas para desencadenar un comando. Un ejemplo de un enlace de doble tecla es <strong>Ctrl *+</strong> k <strong>,</strong>Ctrl <strong>+</strong> k** para establecer un marcador.

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
|editor|Obligatorio. El GUID del editor indica el contexto de edición para el que este método abreviado de teclado estará activo. El valor de ámbito de enlace global es "guidVSStd97".|
|key1|Obligatorio. Entre los valores válidos se incluyen todos los typable alfanuméricos y los valores hexadecimales de dos dígitos precedidos de 0x y [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Opcional. Cualquier combinación de **Ctrl**, **Alt** y **MAYÚS** separadas por espacio.|
|key2|Opcional. Entre los valores válidos se incluyen todos los typable alfanuméricos y los valores hexadecimales de dos dígitos precedidos de 0x y [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Opcional. Cualquier combinación de **Ctrl**, **Alt** y **MAYÚS** separadas por espacio.|
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
|[KeyBindings (elemento)](../extensibility/keybindings-element.md)|Agrupa los elementos KeyBinding y otras agrupaciones de enlaces de teclado.|

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
- [KeyBindings (elemento)](../extensibility/keybindings-element.md)
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
