---
title: "RequiredPlatformVersion (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# RequiredPlatformVersion (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica la versión mínima del sistema operativo que requiere la plantilla de proyecto para que funcione correctamente. Este elemento se utiliza para plantillas de proyecto que crean [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.  
  
 El `RequiredPlatformVersion` valor se compara directamente con la versión del sistema operativo. Si la `RequiredPlatformVersion` es mayor que la versión del sistema operativo, la plantilla no aparece en el **nuevo proyecto** cuadro de diálogo. Para especificar una plantilla para [!INCLUDE[win8](../debugger/includes/win8_md.md)] o posterior, establezca `RequiredPlatformVersion` a 6.2.0. Para especificar una plantilla para [!INCLUDE[win81](../debugger/includes/win81_md.md)] o superior, establezca RequiredPlatformVersion a 6.3.0.  
  
 Plantillas que especifican `RequiredPlatformVersion`\= 8 son compatibles con el cliente anterior [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] plantillas.  
  
 VSTemplate  
TemplateData  
…..TargetPlatformName  
RequiredPlatformVersion  
  
## Sintaxis  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## Atributos y elementos  
 Ninguno.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica la plataforma a la que está orientada la plantilla del proyecto.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
## Comentarios  
 Este texto especifica la versión de sistema operativo mínimo requerida por la plantilla.  
  
## Ejemplo  
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
  
## Vea también  
 [TargetPlatformName \(Elemento, Plantillas de Visual Studio\)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)