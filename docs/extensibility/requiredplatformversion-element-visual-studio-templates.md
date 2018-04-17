---
title: RequiredPlatformVersion (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35a8dc6fa57dbe88ce1e30e9be58105f28fe5641
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion (Elemento, Plantillas de Visual Studio)
Especifica la versión mínima del sistema operativo que requiere la plantilla de proyecto para que funcione correctamente. Este elemento se utiliza para plantillas de proyecto que crean [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.  
  
 El `RequiredPlatformVersion` valor se compara directamente con la versión del sistema operativo. Si el `RequiredPlatformVersion` es mayor que la versión del sistema operativo, la plantilla no aparece en la **nuevo proyecto** cuadro de diálogo. Para especificar una plantilla para [!INCLUDE[win8](../debugger/includes/win8_md.md)] o superior, establezca `RequiredPlatformVersion` a 6.2.0. Para especificar una plantilla para [!INCLUDE[win81](../debugger/includes/win81_md.md)] o superior, establezca RequiredPlatformVersion a 6.3.0.  
  
 Plantillas que especifican `RequiredPlatformVersion`= 8 son compatibles con el cliente anterior [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] plantillas.  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 Ninguno.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica la plataforma a la que está orientada la plantilla del proyecto.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
## <a name="remarks"></a>Comentarios  
 Este texto especifica la versión mínima del sistema operativo requerida por la plantilla.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo especifica que la plantilla del proyecto está orientada a [!INCLUDE[win8](../debugger/includes/win8_md.md)] o posterior.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [TargetPlatformName (elemento) (plantillas de Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)