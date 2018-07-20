---
title: Elemento Assembly (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 195faf23ecb2fca019b4948b3150ab6f9c00f5ec
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155469"
---
# <a name="assembly-element-visual-studio-templates"></a>Elemento Assembly (plantillas de Visual Studio)
Especifica información sobre un ensamblado, que usa la plantilla para agregar una referencia de ensamblado a los proyectos.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Referencias >  
 \<Referencia >  
 \<Ensamblado >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Assembly> AssemblyName </Assembly>  
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
|[Referencia](../extensibility/reference-element-visual-studio-templates.md)|Especifica la referencia de ensamblado para agregar cuando el elemento se agrega a un proyecto.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 Este texto especifica el ensamblado para agregar a un proyecto cuando se crea una instancia de la plantilla de elemento. Este nombre de ensamblado debe especificarse en una de las maneras siguientes:  
  
-   Como un nombre completo del ensamblado. Por ejemplo:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Como referencia de texto simple. Por ejemplo:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Comentarios  
 `Assembly` es un elemento secundario obligatorio de `Reference`.  
  
 El `Reference`, `References,` y `Assembly` elementos solo se pueden utilizar en *.vstemplate* los archivos que tienen un `Type` valor del atributo `Item`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente ilustra la `TemplateContent` elemento de una plantilla de elemento. Este código XML agrega las referencias a la *System.dll* y *System.Data.dll* ensamblados.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)