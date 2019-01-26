---
title: '&lt;formRegion&gt; elemento (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 33bc2ce58f90f37a1219427558a01bd13e5654df
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875343"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elemento (desarrollo de Office en Visual Studio)
  El `formRegion` elemento de la `vstov4` espacio de nombres identifica un área de formulario de Microsoft Office Outlook que está asociado con un complemento de VSTO.

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
 En el siguiente ejemplo de código se muestra un elemento `formRegion` en un manifiesto de aplicación para un complemento de VSTO de Outlook implementado mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Hay tres clases de mensajes asociadas a esta área de formulario. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Vea también

- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)