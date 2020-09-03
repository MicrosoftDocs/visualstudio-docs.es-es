---
title: ProjectItem (elemento, plantillas de elementos de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 885d0fbb50204f23a30fa43c1ffad45c9d67f829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770729"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem (Elemento, Plantillas de elementos de Visual Studio)
Especifica un archivo que se incluye en la plantilla de elemento.

> [!NOTE]
> El `ProjectItem` elemento acepta distintos atributos dependiendo de si la plantilla es para un proyecto o un elemento. En este tema se explica el `ProjectItem` elemento del elemento. Para obtener una explicación del `ProjectItem` elemento de las plantillas de proyecto, vea [ProjectItem (elemento, plantillas de proyecto de Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Sintaxis

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

| Atributo | Descripción |
|---------------------| - |
| `SubType` | Atributo opcional.<br /><br /> Especifica el subtipo de un elemento de una plantilla de elementos de varios archivos. Este valor se usa para determinar el editor que usará [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para abrir el elemento. |
| `CustomTool` | Atributo opcional.<br /><br /> Establece CustomTool para el elemento en el archivo de proyecto. |
| `ItemType` | Atributo opcional.<br /><br /> Establece el ItemType para el elemento en el archivo de proyecto. |
| `ReplaceParameters` | Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento tiene valores de parámetro que deben reemplazarse cuando se crea un proyecto a partir de la plantilla. El valor predeterminado es `false`. |
| `TargetFileName` | Atributo opcional.<br /><br /> Especifica el nombre del elemento que se crea a partir de la plantilla. Este atributo es útil para usar el reemplazo de parámetros con el fin de crear un nombre de elemento. |

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Un `string` que representa el nombre de un archivo en el archivo *. zip* de la plantilla.

## <a name="remarks"></a>Observaciones
 `ProjectItem` es un elemento secundario opcional de `TemplateContent` .

 El `TargetFileName` atributo se puede usar para cambiar el nombre de los archivos con parámetros. Por ejemplo, si el archivo *. VB* existe en el directorio raíz del archivo *. zip* de plantilla, pero desea que el archivo tenga un nombre basado en el nombre de archivo proporcionado por el usuario en el cuadro de diálogo **Agregar nuevo elemento** , usaría el siguiente código XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Cuando se crea un elemento a partir de esta plantilla, el nombre de archivo se basará en el nombre especificado por el usuario en el cuadro de diálogo **Agregar nuevo elemento** . Esto resulta útil al crear plantillas de elementos de varios archivos. Para obtener más información, vea [Cómo: crear plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md) y [parámetros de plantilla](../ide/template-parameters.md).

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
- [Cómo: Crear plantillas de elemento de varios archivos](../ide/how-to-create-multi-file-item-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
