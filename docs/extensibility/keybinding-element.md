---
title: Elemento KeyBinding (Elemento KeyBinding) Microsoft Docs
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
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703141"
---
# <a name="keybinding-element"></a>Elemento KeyBinding
El elemento KeyBinding especifica los métodos abreviados de teclado para los comandos.

 Los comandos pueden tener enlaces de clave simple y doble asociados a ellos. Un ejemplo de un enlace de una sola tecla es **Ctrl**+**S** para el **comando Guardar.** Los enlaces de teclas dobles requieren dos combinaciones de teclas sucesivas para desencadenar un comando. Un ejemplo de un enlace de doble tecla es <strong>Ctrl*+</strong>K<strong>,</strong>Ctrl<strong>+</strong>K** para establecer un marcador.

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
|editor|Necesario. El GUID del editor indica el contexto de edición para el que estará activo este método abreviado de teclado. El valor de ámbito de enlace global es "guidVSStd97".|
|key1|Necesario. Los valores válidos incluyen todos los alfanuméricos tipificables y también los valores hexadecimales de dos dígitos precedidos por 0x y [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Opcional. Cualquier combinación de **Ctrl**, **Alt**y **Mayús** separados por espacio.|
|key2|Opcional. Los valores válidos incluyen todos los alfanuméricos tipificables y también los valores hexadecimales de dos dígitos precedidos por 0x y [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Opcional. Cualquier combinación de **Ctrl**, **Alt**y **Mayús** separados por espacio.|
|emulator|Opcional.|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent||
|Anotación||

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Agrupa KeyBinding elementos y otras keyBindings agrupaciones.|

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
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
