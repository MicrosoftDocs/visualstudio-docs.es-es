---
title: ProjectItem (elemento) (plantillas de elemento de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de479c78d5699fc904174368044a82af5dd64103
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980731"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem (elemento) (plantillas de elemento de Visual Studio)
Especifica un archivo que se incluye en la plantilla de elemento.  
  
> [!NOTE]
>  El `ProjectItem` elemento acepta atributos diferentes dependiendo de si la plantilla es para un proyecto o un elemento. Este tema se explica el `ProjectItem` (elemento) para el elemento. Para obtener una explicación de la `ProjectItem` (elemento) para las plantillas de proyecto, vea [ProjectItem (elemento) (plantillas de proyecto de Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent>  
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
| `SubType` | Atributo opcional.<br /><br /> Especifica el subtipo de un elemento en una plantilla de elementos de varios archivos. Este valor se utiliza para determinar el editor que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizará para abrir el elemento. |
| `CustomTool` | Atributo opcional.<br /><br /> Establece el CustomTool para el elemento en el archivo de proyecto. |
| `ItemType` | Atributo opcional.<br /><br /> Establece el tipo de elemento para el elemento en el archivo de proyecto. |
| `ReplaceParameters` | Atributo opcional.<br /><br /> Un valor booleano que especifica si el elemento tiene valores de parámetro que se deben reemplazar cuando se crea un proyecto de la plantilla. El valor predeterminado es `false`. |
| `TargetFileName` | Atributo opcional.<br /><br /> Especifica el nombre del elemento que se crea a partir de la plantilla. Este atributo es útil para el uso de reemplazo de parámetros para crear un nombre de elemento. |
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 Un `string` que representa el nombre de un archivo en la plantilla *.zip* archivo.  
  
## <a name="remarks"></a>Comentarios  
 `ProjectItem` es un elemento secundario opcional de `TemplateContent`.  
  
 El `TargetFileName` atributo se puede usar para cambiar el nombre de los archivos con parámetros. Por ejemplo, si el archivo *MyFile.vb* existe en el directorio raíz de la plantilla *.zip* archivo, pero desea según el nombre de archivo proporcionado por el usuario en el archivo se denomine el **Agregar nuevo elemento**  cuadro de diálogo, usaría el siguiente código XML:  
  
```xml  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Cuando se crea un elemento de esta plantilla, el nombre de archivo se basará en el nombre del usuario especificado en el **Agregar nuevo elemento** cuadro de diálogo. Esto es útil al crear plantillas de elementos de varios archivos. Para obtener más información, vea [Cómo: Creación de plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md) y [parámetros de plantilla](../ide/template-parameters.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos de la plantilla de elemento estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] clase.  
  
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
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)   
 [Cómo: Creación de plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)