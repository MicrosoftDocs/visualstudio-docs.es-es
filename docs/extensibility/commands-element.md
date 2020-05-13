---
title: Elemento de comandos de comandos de comandos de Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739693"
---
# <a name="commands-element"></a>Elemento Commands
Representa la colección de comandos de la barra de herramientas de VSPackage. La colección puede tener hasta cinco subsecciones, como se indica a continuación: menús, grupos, botones, combos y mapas de bits.

 Cada elemento secundario de subsección, por ejemplo, \<Menu>, se identifica mediante un identificador de comando único que es un PAR de identificador esunidy y GUID. El GUID identifica el "conjunto de comandos" y se utiliza para agrupar comandos relacionados lógicamente. El VSPackage debe definir su propio conjunto de comandos para evitar colisiones con los iDs de comando definidos por otros VSPackages.

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
|paquete|GUID que identifica el VSPackage que proporciona los comandos.<br /><br /> Por ejemplo, package-"guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|
|[Elemento Grupos](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos en un VSPackage.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos De botón de grupos.|
|[Elemento Mapas de bits](../extensibility/bitmaps-element.md)|Agrupa elementos de mapa de bits.|
|[Elemento Combos](../extensibility/combos-element.md)|Agrupa elementos Combo.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un VSPackage proporciona al IDE. Los elementos posibles son elementos de menú, menús, barras de herramientas y cuadros combinados.|

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo utilizar un [elemento Commands](../extensibility/commands-element.md).

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

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agregan elementos de interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
