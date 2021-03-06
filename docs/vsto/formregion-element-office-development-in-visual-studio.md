---
description: El elemento formRegion del espacio de nombres vstov4 identifica una Microsoft Office área de formulario de Outlook que está asociada a un complemento de VSTO.
title: '&lt;&gt;elemento formRegion (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0851ba9e117b464d3a2fbb9ad9903af17ceda0c4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221085"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento formRegion (desarrollo de Office en Visual Studio)
  El `formRegion` elemento del `vstov4` espacio de nombres identifica un Microsoft Office área de formulario de Outlook que está asociada a un complemento de VSTO.

## <a name="syntax"></a>Sintaxis

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `formRegion` del espacio de nombres `vstov4` identifica un área de formulario asociada a un complemento de VSTO de Outlook. Solo es obligatorio para complementos VSTO de Outlook que incluyen áreas de formulario.

 Puede haber varios elementos `formRegion` definidos dentro de un elemento `formRegions` para un único complemento de VSTO.

 El elemento `formRegion` tiene el siguiente atributo.

|Atributo|Descripción|
|---------------|-----------------|
|`name`|Obligatorio. Identifica el nombre del área de formulario.|

 El elemento `formRegion` tiene los siguientes elementos secundarios.

### <a name="messageclass"></a>messageClass
 El elemento `messageClass` identifica el formulario de Outlook que está asociado al área de formulario.

 El elemento `messageClass` tiene el siguiente atributo.

|Atributo|Descripción|
|---------------|-----------------|
|`name`|Obligatorio. Identifica el formulario asociado a este área de formulario.|

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo de código se muestra un elemento `formRegion` en un manifiesto de aplicación para un complemento de VSTO de Outlook implementado mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Hay tres clases de mensajes asociadas a esta área de formulario. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Consulte también

- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
