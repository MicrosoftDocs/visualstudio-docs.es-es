---
title: Providedefaultname ((elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento Providedefaultname (y cómo especifica si Visual Studio generará un nombre predeterminado de Visual Studio en el cuadro de diálogo Agregar nuevo elemento o nuevo proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d29ca3075ee6e5ef031bb360ecfd10d6cb341c26
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068652"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Providedefaultname ((elemento, plantillas de Visual Studio)
Especifica si el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sistema del proyecto generará un nombre predeterminado para la plantilla en el cuadro de diálogo **Agregar nuevo elemento** o **nuevo proyecto** .

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Sintaxis

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser `true` o `false` , lo que indica si se va a generar un nombre predeterminado para la plantilla en el cuadro de diálogo **Agregar nuevo elemento** o **nuevo proyecto** .

## <a name="remarks"></a>Observaciones
 `ProvideDefaultName` es un elemento opcional. El valor predeterminado es `true`.

 Si el `ProvideDefaultName` elemento es `false` , los cuadros de **nombre** de los cuadros de diálogo **Agregar nuevo elemento** y **nuevo proyecto** contienen el valor `<Enter_name>` .

 Use el elemento [defaultname (](../extensibility/defaultname-element-visual-studio-templates.md) para especificar el nombre predeterminado del proyecto o elemento en los cuadros de diálogo **Agregar nuevo elemento** y **nuevo proyecto** . Cuando el valor del `ProvideDefaultName` elemento es `true` , la omisión del `DefaultName` elemento para los proyectos rellena el cuadro de diálogo con el nombre de la plantilla, es decir, el valor del elemento [Name](../extensibility/name-element-visual-studio-templates.md) .

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente `ProvideDefaultName` se establece el elemento en `false` .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
