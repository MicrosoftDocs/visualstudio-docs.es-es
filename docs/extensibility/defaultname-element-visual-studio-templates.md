---
title: Defaultname ((elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento Defaultname (y cómo especifica el nombre que generará el sistema del proyecto de Visual Studio para el proyecto o elemento cuando se crea.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23defc424d3e7ed5095f0e29d673c191c755f9ce
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672735"
---
# <a name="defaultname-element-visual-studio-templates"></a>Defaultname ((elemento, plantillas de Visual Studio)
Especifica el nombre que generará el sistema del proyecto de Visual Studio para el proyecto o elemento cuando se crea.

 \<VSTemplate> \<TemplateData>
 \<DefaultName>

## <a name="syntax"></a>Sintaxis

```
<DefaultName>
    Default Project Name
</DefaultName>
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

 Este texto especifica el nombre predeterminado del proyecto o elemento.

## <a name="remarks"></a>Comentarios
 `DefaultName` es un elemento opcional.

 En el caso de los proyectos, este elemento especifica el nombre del directorio que almacena el proyecto en el disco. En el caso de los elementos, especifica el nombre de archivo del archivo de código fuente.

 Al crear un proyecto o elemento, puede modificar el nombre predeterminado mediante la opción **nombre** , que está disponible en el cuadro de diálogo **nuevo proyecto** o en el cuadro de diálogo **Agregar nuevo elemento** .

 Si no desea que el sistema del proyecto genere el nombre predeterminado para el proyecto o elemento, establezca el elemento [providedefaultname (](../extensibility/providedefaultname-element-visual-studio-templates.md) en `False` .

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de la plantilla de elemento estándar para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] clase.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
