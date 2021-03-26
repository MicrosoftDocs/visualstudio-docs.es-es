---
title: Commands (elemento) | Microsoft Docs
description: 'El elemento Commands representa la colección de comandos de la barra de herramientas de VSPackage y puede tener estas secciones: menús, grupos, botones, cuadros combinados y mapas de bits.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 671e855a31af17310fdab58689d8775b490cb93a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089594"
---
# <a name="commands-element"></a>Elemento Commands
Representa la colección de comandos de la barra de herramientas de VSPackage. La colección puede tener hasta cinco subsecciones, como se indica a continuación: menús, grupos, botones, cuadros combinados y mapas de bits.

 Cada elemento secundario de subsección, por ejemplo,, \<Menu> se identifica mediante un identificador de comando único que es un par de identificador GUID y numérico. El GUID identifica el "conjunto de comandos" y se utiliza para agrupar comandos relacionados lógicamente. El VSPackage debe definir su propio conjunto de comandos para evitar colisiones con los identificadores de comando definidos por otros VSPackages.

## <a name="syntax"></a>Sintaxis

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|paquete|GUID que identifica el VSPackage que proporciona los comandos.<br /><br /> Por ejemplo, package = "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Menus (elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos en un VSPackage.|
|[Buttons, elemento](../extensibility/buttons-element.md)|Agrupa los elementos de botón.|
|[Elemento bitmaps](../extensibility/bitmaps-element.md)|Agrupa los elementos de mapa de bits.|
|[Comboboxs (elemento)](../extensibility/combos-element.md)|Agrupa los elementos combinados.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un VSPackage proporciona al IDE. Los elementos posibles son elementos de menú, menús, barras de herramientas y cuadros combinados.|

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo usar un [elemento Commands](../extensibility/commands-element.md).

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Consulte también
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
