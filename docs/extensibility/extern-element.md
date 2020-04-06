---
title: Elemento Extern (Elemento externo) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711486"
---
# <a name="extern-element"></a>Elemento Externo
El elemento Extern hace referencia a cualquier archivo de encabezado externo (*.h*) para combinar con el archivo *.vsct* en tiempo de compilación. Los archivos que se van a combinar deben estar en la ruta de acceso Include dada al compilador VSCT o a la que hace referencia un [elemento Include](../extensibility/include-element.md). Los archivos pueden ser otros archivos *.vsct* o archivos de encabezado C++.

 Las definiciones de los archivos de encabezado deben tener el formato "#define [Símbolo] [Valor]" El valor puede ser otro símbolo si está definido previamente. Las definiciones se pueden utilizar en instrucciones condicionales de elementos de comando. Cualquier símbolo que no se utilice realmente será descartado.

 CommandTable Element Extern Element

## <a name="syntax"></a>Sintaxis

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|href|Necesario. La ruta de acceso al archivo de encabezado:<br /><br /> href"stdidcmd.h"|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Opcional. El idioma predeterminado [ \<](../extensibility/strings-element.md) de todas las cadenas>elementos de la tabla de comandos:<br /><br /> "en-nosotros"|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno.|Ninguno.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos (es decir, elementos de menú, menús, barras de herramientas y cuadros combinados) que un VSPackage proporciona al IDE.|

## <a name="example"></a>Ejemplo

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Cómo VSPackages agregan elementos de interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
