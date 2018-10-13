---
title: RequiredPlatformVersion (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4b3ca2e03b79f2cb1fcdcc738a88e3945d95972f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276060"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica la versión mínima del sistema operativo que requiere la plantilla de proyecto para que funcione correctamente. Este elemento se usa para plantillas de proyecto que creen [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplicaciones.  
  
 El `RequiredPlatformVersion` valor se compara directamente con la versión del sistema operativo. Si el `RequiredPlatformVersion` es mayor que la versión del sistema operativo, la plantilla no aparece en el **nuevo proyecto** cuadro de diálogo. Para especificar una plantilla para [!INCLUDE[win8](../includes/win8-md.md)] o superior, establezca `RequiredPlatformVersion` a la 6.2.0. Para especificar una plantilla para [!INCLUDE[win81](../includes/win81-md.md)] o superior, establezca RequiredPlatformVersion a 6.3.0.  
  
 Las plantillas que especifican `RequiredPlatformVersion`= 8 son compatibles con clientes anteriores [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] plantillas.  
  
 VSTemplate  
TemplateData  
... TargetPlatformName  
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
 Este ejemplo especifica que la plantilla del proyecto está orientada a [!INCLUDE[win8](../includes/win8-md.md)] o posterior.  
  
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

