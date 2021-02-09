---
title: Referencia de esquemas de elementos de proyecto de SharePoint | Microsoft Docs
description: Vea una introducción a la referencia de esquemas XML del elemento de proyecto de SharePoint (ProjectItemModelSchema. xsd), que se usa para validar el contenido de los archivos. spdata.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 466bc68ca002914b64698d7cd87f98ff276bfc0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892286"
---
# <a name="sharepoint-project-item-schema-reference"></a>Referencia de esquemas de elementos de proyecto de SharePoint
  Visual Studio usa el esquema de elementos de proyecto de SharePoint para validar el contenido de los archivos *. spdata* . Un archivo *. spdata* especifica el contenido y el comportamiento de un elemento de proyecto de SharePoint. Para obtener más información sobre el contenido de los elementos de proyecto de SharePoint, vea [crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 El esquema del elemento de proyecto de SharePoint se denomina ProjectItemModelSchema. xsd y se instala de forma predeterminada en% archivos de programa (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.

 El elemento raíz es el elemento [ProjectItem](../sharepoint/projectitem-element.md) . En la tabla siguiente se describen todos los elementos definidos por el esquema.

|Elemento|Descripción|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa una colección de elementos de datos personalizados que están asociados al elemento de proyecto de SharePoint.|
|[Extensiondataitem (](../sharepoint/extensiondataitem-element.md)|Representa un elemento de datos personalizado que está asociado al elemento de proyecto de SharePoint, en formato de clave y valor. La clave y el valor deben ser cadenas.|
|[Featureproperties (](../sharepoint/featureproperties-element.md)|Representa una colección de valores de propiedad que se incluyen con una característica cuando se implementa en SharePoint. Una vez implementada una característica, puede tener acceso a los valores de propiedad en el código.|
|[Featureproperty (](../sharepoint/featureproperty-element.md)|Representa una propiedad personalizada que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada una característica, puede tener acceso a la propiedad en el código.|
|[Archivos](../sharepoint/files-element.md)|Especifica los archivos que se van a implementar con el elemento de proyecto de SharePoint, como un archivo de elemento de característica o la salida de un proyecto.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint.|
|[Projectitemfile (](../sharepoint/projectitemfile-element.md)|Representa un archivo de SharePoint, como el archivo de elemento de característica, que se va a incluir con el elemento de proyecto cuando se implemente en SharePoint.|
|[Projectitemfolder (](../sharepoint/projectitemfolder-element.md)|Representa una carpeta asignada.|
|[ProjectOutputFile (](../sharepoint/projectoutputfile-element.md)|Representa la salida de un proyecto que se incluirá con el elemento de proyecto cuando se implemente en SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Representa un control ASPX o un elemento Web que se designa como seguro para que cualquier usuario tenga acceso a cualquier página ASPX del sitio de SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa una colección de controles ASPX y elementos web que se designan como seguros para que cualquier usuario tenga acceso a cualquier página ASPX en el sitio de SharePoint.|

## <a name="see-also"></a>Vea también
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
