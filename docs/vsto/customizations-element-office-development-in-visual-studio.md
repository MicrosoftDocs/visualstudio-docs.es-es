---
title: '&lt;personalizaciones&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9ac1a78f0d35b2fac751e87874bbfe169798712a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673922"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;personalizaciones&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `customizations` del espacio de nombres `vstov4` contiene toda la información sobre la instalación y carga de cada solución de Office.  
  
## <a name="syntax-for-document-level-customizations"></a>Sintaxis para las personalizaciones de nivel de documento  
  
```xml
<customizations>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</customizations>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Sintaxis de los complementos de VSTO  
  
```xml
<customizations>  
  <customization  
    id  
    <appAddin  
      application  
      loadBehavior  
      keyName>  
    <friendlyName></friendlyName>  
    <description></description>  
    <formRegions></formRegions>  
  </customization>  
</customizations>  
```  
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
 El elemento `customizations` contiene información específica sobre cada solución de Office. Este elemento debe estar en el espacio de nombres siguiente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Los elementos secundarios del ensamblado también deben estar en este espacio de nombres.  
  
 El elemento `customizations` no tiene atributos.  
  
 El elemento `customizations` tiene el siguiente elemento secundario:  
  
### <a name="customization"></a>Personalización  
 Requerido. El `customization` elemento en el `vstov4` espacio de nombres se define en [ &#60;personalización&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Ejemplo de una personalización de nivel de documento  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra el elemento `customizations` para una personalización de nivel de documento.  
  
> [!NOTE]  
>  Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:document   
      solutionId="73e" />  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="example-of-a-vsto-add-in"></a>Ejemplo de un complemento de VSTO  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se ilustra la `customizations` (elemento) para un complemento de VSTO. Este es un complemento de VSTO para Outlook que incluye áreas de formulario. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:appAddIn   
      application="Outlook"   
      loadBehavior="3"   
      keyName="ContosoOutlookAddIn">  
      <vstov4:friendlyName>  
        ContosoOutlookAddIn  
      </vstov4:friendlyName>  
      <vstov4:description>  
        ContosoOutlookAddIn - Outlook VSTO Add-in   
        created with Visual Studio Tools for Office  
      </vstov4:description>  
      <vstov4:formRegions>  
        <vstov4:formRegion  
            name="OutlookAddIn1.FormRegion1">  
          <vstov4:messageClass name="IPM.Note" />  
          <vstov4:messageClass name="IPM.Contact" />  
          <vstov4:messageClass name="IPM.Appointment" />  
        </vstov4:formRegion>  
      </vstov4:formRegions>  
    </vstov4:appAddIn>  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  