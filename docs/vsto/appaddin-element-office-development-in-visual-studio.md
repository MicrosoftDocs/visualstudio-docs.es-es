---
title: '&lt;appAddin&gt; elemento (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2116576acb06e6291749d9c0176fcf4ebb426739
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953249"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elemento (desarrollo de Office en Visual Studio)
  El **appAddin** elemento de la `vstov4` espacio de nombres almacena información específica de la personalización para complementos VSTO.

## <a name="syntax"></a>Sintaxis

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El **appAddin** elemento es necesario y se encuentra en la `vstov4` espacio de nombres. Solo hay un **appAddin** elemento definido en un manifiesto de aplicación.

 El **appAddin** elemento tiene los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|**application**|Obligatorio. Identifica la aplicación de Microsoft Office. El valor puede ser uno de los siguientes: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|
|**loadBehavior**|Opcional. De forma predeterminada, el **loadBehavior** se habilita al establecer este valor. Para la depuración, el complemento de VSTO puede deshabilitarse si establece el valor en dos. Para obtener más información, vea la tabla denominada LoadBehavior Values en [entradas del registro para complementos VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Obligatorio. Este valor es el nombre de clave del Registro que la aplicación utilizará para cargar el complemento de VSTO. Para obtener más información, consulte [entradas del registro para complementos VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 El **appAddin** elemento tiene los siguientes elementos secundarios.

### <a name="friendlyname"></a>friendlyName
 Opcional. El **friendlyName** elemento se explica en [ &#60;friendlyName&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description
 Opcional. El **descripción** elemento se explica en [ &#60;descripción&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario. El **formRegions** elemento se explica en [ &#60;formRegions&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="description"></a>Descripción
 El siguiente ejemplo de código ilustra **appAddin** elementos en una solución de Outlook implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
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
```

## <a name="see-also"></a>Vea también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)