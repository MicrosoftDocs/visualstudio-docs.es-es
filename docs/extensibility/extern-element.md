---
title: Elemento Extern | Microsoft Docs
description: El elemento Extern hace referencia a cualquier archivo de encabezado externo (.h) para combinar con el archivo .vsct en tiempo de compilación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 502b93f18aacfed26d3ea440c017e6de5281a35d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900192"
---
# <a name="extern-element"></a>Elemento Extern
El elemento Extern hace referencia a cualquier archivo de encabezado externo (*.h*) para combinar con *el archivo .vsct* en tiempo de compilación. Los archivos que se deben combinar deben estar en la ruta de acceso include dada al compilador de VSCT o a la que hace referencia un [elemento Include](../extensibility/include-element.md). Los archivos pueden ser otros *archivos .vsct* o archivos de encabezado de C++.

 Las definiciones de los archivos de encabezado deben tener el formato "#define [Símbolo] [Valor]" El valor puede ser otro símbolo si se ha definido previamente. Las definiciones se pueden usar en instrucciones condicionales de elementos de comando. Se descartará cualquier símbolo que no se utilice realmente.

 Elemento CommandTable Extern

## <a name="syntax"></a>Sintaxis

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|href|Necesario. Ruta de acceso al archivo de encabezado:<br /><br /> href="stdidcmd.h"|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|
|language|Opcional. Idioma predeterminado de todos los [\<Strings>](../extensibility/strings-element.md) elementos de la tabla de comandos:<br /><br /> language="en-us"|

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
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Cómo agregan vsPackages elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
