---
title: '&lt;&gt;elemento appAddin (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: 1bf9ea990d12bd24adee3f6a24a39fa43c74fb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531643"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento appAddin (desarrollo de Office en Visual Studio)
  El elemento **appAddin** del `vstov4` espacio de nombres almacena información específica de la personalización de los complementos de VSTO.

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
 El elemento **appAddin** es obligatorio y se encuentra en el `vstov4` espacio de nombres. Solo hay un elemento **appAddin** definido en un manifiesto de aplicación.

 El elemento **appAddin** tiene los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|**application**|Necesario. Identifica la aplicación de Microsoft Office. El valor puede ser uno de los siguientes: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|
|**loadBehavior**|Opcional. De forma predeterminada, **loadBehavior** se habilita estableciendo este valor en. Para la depuración, el complemento de VSTO puede deshabilitarse si establece el valor en dos. Para obtener más información, vea la tabla titulada valores de LoadBehavior en [entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Necesario. Este valor es el nombre de clave del Registro que la aplicación utilizará para cargar el complemento de VSTO. Para obtener más información, vea [entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 El elemento **appAddin** tiene los siguientes elementos secundarios.

### <a name="friendlyname"></a>friendlyName
 Opcional. El elemento **friendlyName** se explica en [&#60;friendlyName&#62; elemento &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description
 Opcional. El elemento **Description** se explica en [&#60;descripción&#62; elemento &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Solo es obligatorio para los complementos de VSTO de Outlook que incluyan áreas del formulario. El elemento **FormRegions** se explica en [&#60;elemento&#62; FormRegions &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se muestran los elementos **appAddin** en una solución de Outlook implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)