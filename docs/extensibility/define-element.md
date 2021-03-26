---
title: Definir elemento | Microsoft Docs
description: El elemento define define un par de nombre y valor de símbolo. Este símbolo puede ser evaluado por atributos condicionales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83a8ee40205cafcaff29399ead4036374f798abf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082275"
---
# <a name="define-element"></a>Elemento define
Define un par de nombre y valor de símbolo. Este símbolo puede ser evaluado por atributos condicionales. Para obtener más información, vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md). Vea también el [elemento Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Sintaxis

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|name|Necesario. El nombre del símbolo:<br /><br /> Name = "MODE"|
|value|Necesario. El valor del símbolo:<br /><br /> valor = "estándar"|
|Condición|Opcional. Para obtener más información, vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos que un VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados.|

## <a name="example"></a>Ejemplo

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
