---
title: Referencia de esquema de elemento de proyecto de SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007724"
---
# <a name="sharepoint-project-item-schema-reference"></a>Referencia de esquemas de elemento de proyecto de SharePoint
  Visual Studio usa el esquema de elemento de proyecto de SharePoint para validar el contenido de *.spdata* archivos. Un *.spdata* archivo especifica el contenido y el comportamiento de un elemento de proyecto de SharePoint. Para obtener más información sobre el contenido de los elementos de proyecto de SharePoint, vea [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 El esquema de elemento de proyecto de SharePoint se denomina ProjectItemModelSchema.xsd y se instala de forma predeterminada en % archivos de programa (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.

 El elemento raíz es el [ProjectItem](../sharepoint/projectitem-element.md) elemento. En la tabla siguiente se describe todos los elementos definidos por el esquema.

|Elemento|Descripción|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa una colección de elementos de datos personalizados que están asociados con el elemento de proyecto de SharePoint.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Representa un elemento de datos personalizado que está asociado con el elemento de proyecto de SharePoint, en formato de clave/valor. La clave y el valor deben ser cadenas.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Representa una colección de valores de propiedad que se incluyen con una característica cuando se implementa en SharePoint. Una vez implementada la característica, puede tener acceso a los valores de propiedad en el código.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Representa una propiedad personalizada que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada la característica, puede tener acceso a la propiedad en el código.|
|[Archivos](../sharepoint/files-element.md)|Especifica los archivos para implementar con el elemento de proyecto de SharePoint, como un archivo de elemento de característica o la salida de un proyecto.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Representa un archivo de SharePoint, como archivo de elemento de característica, se incluyen con el elemento de proyecto cuando se implementa en SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Representa una carpeta asignada.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Representa la salida de un proyecto para incluir con el elemento de proyecto cuando se implementa en SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Representa un control ASPX o elemento Web que se designa como seguro para que cualquier usuario tenga acceso en cualquier página ASPX del sitio de SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa una colección de controles ASPX y elementos Web que se designan como seguros para cualquier usuario tenga acceso en cualquier página ASPX del sitio de SharePoint.|

## <a name="see-also"></a>Vea también
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
