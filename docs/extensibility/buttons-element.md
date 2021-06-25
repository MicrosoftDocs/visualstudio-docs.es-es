---
title: Elemento Buttons | Microsoft Docs
description: El elemento Buttons agrupa elementos Button, que representan comandos individuales. Este artículo contiene un ejemplo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2952f9f6747e52604e9f24cd173ab07f8d5a4756
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900803"
---
# <a name="buttons-element"></a>Elemento Buttons
Agrupa [elementos Button,](../extensibility/button-element.md) que representan comandos individuales.

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
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos De botón de grupos.|
|[Elemento Button](../extensibility/button-element.md)|Define un comando con el que el usuario puede interactuar.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Commands](../extensibility/commands-element.md)|Representa la colección de comandos en la barra de herramientas de VSPackage.|

## <a name="example"></a>Ejemplo

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>Consulte también
- [Cómo agregan vsPackages elementos de interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
