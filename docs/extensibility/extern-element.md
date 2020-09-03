---
title: Extern (elemento) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711486"
---
# <a name="extern-element"></a>Extern (elemento)
El elemento extern hace referencia a los archivos de encabezado (*. h*) externos que se van a combinar con el archivo *. Vsct* en tiempo de compilación. Los archivos que se van a combinar deben estar en la ruta de acceso de inclusión que se proporciona al compilador VSCT o a los que hace referencia un [elemento include](../extensibility/include-element.md). Los archivos pueden ser otros archivos *. Vsct* o archivos de encabezado de C++.

 Las definiciones de los archivos de encabezado deben tener el formato "#define [símbolo] [valor]" el valor puede ser otro símbolo si se ha definido previamente. Las definiciones se pueden usar en instrucciones condicionales de elementos de comandos. Se descartará cualquier símbolo que no se use realmente.

 Elemento extern del elemento CommandTable

## <a name="syntax"></a>Sintaxis

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|href|Necesario. La ruta de acceso al archivo de encabezado:<br /><br /> href = "stdidcmd. h"|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Opcional. El idioma predeterminado de todos los [\<Strings>](../extensibility/strings-element.md) elementos de la tabla de comandos:<br /><br /> Language = "en-US"|

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

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
