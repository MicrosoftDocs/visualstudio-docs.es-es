---
title: Elemento SafeControl | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c9936054c5cc622e6f335d81d1568ebed16518f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547932"
---
# <a name="safecontrol-element"></a>SafeControl (elemento)
  Representa un control ASPX o un elemento Web que se designa como seguro para que cualquier usuario tenga acceso a cualquier página ASPX del sitio de SharePoint.

## <a name="syntax"></a>Sintaxis

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|**Assembl**|Atributo **xs: String** opcional.<br /><br /> Nombre del ensamblado en el que se define el control ASPX o el elemento Web. De forma predeterminada, este atributo usa el parámetro **$SharePoint. Project. AssemblyFullName $** reemplazable para el nombre del ensamblado. Para obtener más información, vea [parámetros reemplazables](../sharepoint/replaceable-parameters.md).|
|**IsSafe**|Atributo **xs: Boolean** opcional.<br /><br /> Especifica si el control ASPX o el elemento Web es seguro para que los usuarios que no son de confianza tengan acceso a.|
|**IsSafeAgainstScript**|Atributo **xs: Boolean** opcional.<br /><br /> Especifica si los usuarios que no son de confianza pueden ver o editar las propiedades del control ASPX o del elemento Web.|
|**Name**|Atributo **xs: String** opcional.<br /><br /> Nombre de esta entrada de control segura en la colección.|
|**Espacio de nombres**|Atributo **xs: String** opcional.<br /><br /> Espacio de nombres del control o elemento Web ASPX.|
|**TypeName**|Atributo **xs: String** opcional.<br /><br /> Nombre del tipo del control o elemento Web ASPX.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa una colección de controles ASPX y elementos web que se designan como seguros para que cualquier usuario tenga acceso a cualquier página ASPX en el sitio de SharePoint.|

## <a name="remarks"></a>Observaciones
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
- [Proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
