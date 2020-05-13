---
title: Elemento de los botones (Buttons Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64ac5621093f30af28ade0817906b767231e4ee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739920"
---
# <a name="buttons-element"></a>Elemento Buttons
Elementos [Button](../extensibility/button-element.md) de grupos, que representan comandos individuales.

## <a name="syntax"></a>Sintaxis

```
<Buttons>
  <Button>... </Button>
  <Button>... </Button>
</Buttons>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos De botón de grupos.|
|[Elemento Button](../extensibility/button-element.md)|Define un comando con el que el usuario puede interactuar.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Comandos](../extensibility/commands-element.md)|Representa la colección de comandos de la barra de herramientas de VSPackage.|

## <a name="example"></a>Ejemplo

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>Consulte también
- [Cómo VSPackages agregan elementos de interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
