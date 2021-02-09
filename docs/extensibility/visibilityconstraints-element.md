---
title: Elemento VisibilityConstraints | Microsoft Docs
description: El elemento VisibilityConstraints determina la visibilidad estática de los grupos de comandos y barras de herramientas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb6047c98031c484f6a0a51ab2a393a2a46bb2a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926088"
---
# <a name="visibilityconstraints-element"></a>Elemento VisibilityConstraints
El elemento VisibilityConstraints determina la visibilidad estática de los grupos de comandos y barras de herramientas. La visibilidad se controla primero mediante el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) sin cargar el VSPackage.

## <a name="syntax"></a>Sintaxis

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina la visibilidad estática de los comandos y las barras de herramientas.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilidad estática de grupos de comandos y barras de herramientas.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos (por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados) que un VSPackage proporciona al IDE.|

## <a name="example"></a>Ejemplo

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Vea también
- [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)
- [Tabla de comandos de Visual Studio (. Archivos de Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
