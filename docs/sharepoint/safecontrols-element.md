---
title: SafeControls (elemento) | Microsoft Docs
description: Obtenga información sobre el elemento SafeControls, que contiene una colección de controles ASPX o elementos Web marcados como seguros para el acceso en la página ASPX de un sitio de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 23e31e3df59d6d580ac94ffcb83f7a17e186a267
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889452"
---
# <a name="safecontrols-element"></a>SafeControls (elemento)
  Colección de controles ASPX y elementos web que se designan como seguros para que cualquier usuario tenga acceso a cualquier página ASPX del sitio de SharePoint.

## <a name="syntax"></a>Sintaxis

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Elemento opcional.<br /><br /> Representa un control ASPX o un elemento Web que se designa como seguro para que cualquier usuario tenga acceso a cualquier página ASPX del sitio de SharePoint.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento es el elemento raíz necesario del archivo *. spdata* .|

## <a name="remarks"></a>Notas
 Para obtener más información sobre los controles seguros, vea [proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Consulte también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Inclusión de información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
