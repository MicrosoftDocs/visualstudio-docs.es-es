---
title: Usar módulos para incluir archivos en la solución | Microsoft Docs
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
ms.openlocfilehash: 778bbc9cff2d7853628edbb5be6466acc55d9ab8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015817"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Usar módulos para incluir archivos en la solución
  Puede haber ocasiones en las que desee implementar archivos en el servidor de SharePoint, independientemente de su tipo de archivo, como las nuevas páginas maestras. Para ello, puede usar *módulos* (no debe confundirse con los [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos de código). Los módulos son contenedores de archivos en una solución de SharePoint. Cuando se implementa la solución, los archivos del módulo se copian en las carpetas especificadas en el servidor de SharePoint.

## <a name="module-items-and-elements"></a>Elementos y elementos de módulo
 Para crear un módulo, agréguelo a un proyecto, para lo que debe elegirlo en el cuadro de diálogo **Agregar nuevo elemento** . A continuación, modifique su archivo *Elements.xml* para incluir los nombres de los archivos que desea implementar, dónde se encuentran en el sistema y dónde se deben copiar en el servidor de SharePoint.

 Este es un ejemplo del archivo de *Elements.xml* para un módulo:

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
|*Elements.xml*|El archivo de definición para el módulo.|
|*Sample.txt*|Un archivo de marcador de posición que actúa como ejemplo de un archivo en el módulo.|

 El archivo *Elements.xml* contiene los siguientes elementos:

|Nombre del elemento|Descripción|
|------------------|-----------------|
|Elementos|Contiene todos los elementos definidos en el módulo.|
|Módulo|El elemento Module tiene un único atributo, *Name*, que especifica el nombre del módulo en el formato `<Module Name="Module1">` .<br /><br /> Tenga en cuenta que si cambia el nombre del módulo (o su propiedad *nombre de carpeta* ), debe actualizar manualmente el nombre en el elemento Module.<br /><br /> Si especifica un subdirectorio para los archivos en el elemento Module, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) creará automáticamente una estructura de directorios coincidente para ellos.|
|Archivo|El elemento File tiene dos parámetros, *path* y *URL*.<br /><br /> -Path: el nombre y la ubicación del archivo en la solución de SharePoint. El formato es, `Path="Module1\Sample.txt"` .<br /><br /> -URL: la ubicación en la que se implementará el archivo en el servidor de SharePoint. El formato es, `Url="Module1/Sample.txt"` .<br /><br /> -Type: un atributo opcional que tiene dos valores: *GhostableInLibrary* y *Ghostable*. El formato es, `Type="GhostableInLibrary"` . Especificar *GhostableInLibrary* significa que el archivo se agregará a una biblioteca de documentos de SharePoint junto con un elemento de lista para acompañar el archivo cuando se agrega a la biblioteca. Si se especifica *Ghostable* , el archivo se agrega a SharePoint fuera de la biblioteca de documentos.|

 Cada archivo que desea implementar requiere una `<File>` entrada de elemento independiente en *Elements.xml*.

## <a name="see-also"></a>Consulte también
- [Cómo: incluir archivos mediante un módulo](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Cómo: aprovisionar un archivo](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Desarrollo de soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
