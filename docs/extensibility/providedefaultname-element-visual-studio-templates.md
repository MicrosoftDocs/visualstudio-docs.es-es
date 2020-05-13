---
title: Elemento ProvideDefaultName (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701714"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (plantillas de Visual Studio)
Especifica si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el sistema de proyectos generará un nombre predeterminado para la plantilla en el cuadro de diálogo **Agregar nuevo elemento** o Nuevo **proyecto.**

 \<VSTemplate \<> TemplateData> \<> ProvideDefaultName

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

 El texto debe `true` `false`ser o , que indica si se debe generar o no un nombre predeterminado para la plantilla en el **agregar nuevo elemento** o nuevo **proyecto** cuadro de diálogo.

## <a name="remarks"></a>Observaciones
 `ProvideDefaultName` es un elemento opcional. El valor predeterminado es `true`.

 Si `ProvideDefaultName` el `false`elemento es , los cuadros **Nombre** de los `<Enter_name>`cuadros de diálogo Agregar nuevo **elemento** y Nuevo **proyecto** contienen el valor .

 Utilice el elemento [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) para especificar el nombre predeterminado del proyecto o elemento en los cuadros de diálogo **Agregar nuevo elemento** y Nuevo **proyecto.** Cuando el valor `ProvideDefaultName` del `true`elemento es `DefaultName` , la omisión del elemento para los proyectos rellena el cuadro de diálogo con el nombre de la plantilla, es decir, el valor del elemento [Name.](../extensibility/name-element-visual-studio-templates.md)

## <a name="example"></a>Ejemplo
 En el ejemplo `ProvideDefaultName` de `false`código siguiente se establece el elemento en .

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
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
