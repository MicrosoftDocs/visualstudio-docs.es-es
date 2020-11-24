---
title: Uso de módulos para incluir archivos en la solución | Microsoft Docs
description: Use módulos, o contenedores para archivos en una solución de SharePoint, para implementar archivos en el servidor de SharePoint, independientemente de su tipo de archivo (como páginas maestras).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa0d6fe1855a1d60a0e1293e8422791f8148bd04
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442526"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Uso de módulos para incluir archivos en la solución
  Es posible que en ocasiones quiera implementar archivos en el servidor de SharePoint, independientemente de su tipo de archivo, como nuevas páginas maestras. Para ello, puede usar *Módulos* (no los confunda con los módulos de código de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]). Los módulos son contenedores de archivos en una solución de SharePoint. Cuando se implementa la solución, los archivos del módulo se copian en las carpetas especificadas en el servidor de SharePoint.

## <a name="module-items-and-elements"></a>Elementos y elementos de módulo
 Para crear un módulo, debe elegirlo en el cuadro de diálogo **Agregar nuevo elemento** para agregarlo a un proyecto. Después, modifique su archivo *Elements.xml* para incluir los nombres de los archivos que quiera implementar, dónde se encuentran en el sistema y dónde se deben copiar en el servidor de SharePoint.

 Este es un ejemplo del archivo *Elements.xml* de un módulo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Los módulos recién creados contienen los siguientes archivos predeterminados:

|Nombre de archivo|Descripción|
|---------------|-----------------|
|*Elements.xml*|El archivo de definición del módulo.|
|*Sample.txt*|Un archivo de marcador de posición que actúa como ejemplo de un archivo en el módulo.|

 El archivo *Elements.xml* contiene los elementos siguientes:

|Nombre del elemento|Descripción|
|------------------|-----------------|
|Elementos|Contiene todos los elementos definidos en el módulo.|
|Módulo|El elemento de módulo tiene un solo atributo, *Name*, que especifica el nombre del módulo en el formato `<Module Name="Module1">`.<br /><br /> Tenga en cuenta que si cambia el nombre del módulo (o su propiedad *Nombre de carpeta*), tendrá que actualizar manualmente el nombre en el elemento Módulo.<br /><br /> Si especifica un subdirectorio para los archivos en el elemento Módulo, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) creará automáticamente una estructura de directorios coincidente para ellos.|
|Archivo|El elemento Archivo tiene dos parámetros, *Path* y *Url*.<br /><br /> - Path: nombre y ubicación del archivo en la solución de SharePoint. El formato es `Path="Module1\Sample.txt"`.<br /><br /> - Url: ubicación donde se va a implementar el archivo en el servidor de SharePoint. El formato es `Url="Module1/Sample.txt"`.<br /><br /> - Type: atributo opcional con dos valores: *GhostableInLibrary* y *Ghostable*. El formato es `Type="GhostableInLibrary"`. La especificación de *GhostableInLibrary* significa que el archivo se agregará a una biblioteca de documentos de SharePoint junto con un elemento de lista para acompañar el archivo cuando se agrega a la biblioteca. Al especificar *Ghostable*, el archivo se agrega a SharePoint fuera de la biblioteca de documentos.|

 Cada archivo que quiera implementar necesita una entrada de elemento `<File>` independiente en *Elements.xml*.

## <a name="see-also"></a>Consulte también
- [Cómo: para incluir archivos mediante un módulo](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Procedimiento para aprovisionar un archivo](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Desarrollo de soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
