---
title: '&lt;aplicación&gt; elemento (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b02a3bb762efd9136da79d3128caa0cf8a19f95
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2018
ms.locfileid: "53247776"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;aplicación&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `application` del espacio de nombres `vstav3` contiene la descripción de las soluciones de Office. Los elementos secundarios son diferentes para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
## <a name="syntax-for-document-level-customizations"></a>Sintaxis para las personalizaciones de nivel de documento  
  
```xml 
<application>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</application>  
```  
  
## <a name="syntax-for-application-level-add-ins"></a>Sintaxis para los complementos de nivel de aplicación  
  
```xml
<application>  
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
</application>  
```  
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
 El elemento `application` del espacio de nombres `vstav3` es el nodo que encapsula toda la información específica de la personalización que se encuentra en el espacio de nombres `vstov4` .  
  
 El elemento `application` no tiene atributos.  
  
 El elemento `application` tiene el siguiente elemento:  
  
### <a name="customization"></a>Personalización  
 El rol de la `customization` elemento en el `vstov3` espacio de nombres se define en [ &#60;personalización&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código se muestra un elemento `application` en una solución de Office de nivel de documento implementada con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml  
<vstav3:application>  
  <vstov4:customizations   
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
    <vstov4:customization>  
      <vstov4:document   
        solutionId="73e" />  
    </vstov4:customization>  
  </vstov4:customizations>  
</vstav3:application>  
```  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código se muestra un elemento `application` en una solución de Office de nivel de aplicación implementada con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml  
<vstav3:application>  
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
</vstav3:application>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  