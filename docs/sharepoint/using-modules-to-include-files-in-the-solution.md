---
title: Utilizar módulos para incluir archivos en la solución | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0773d9c167a0a799b7d9bc8ddd2b52afc9bc6f2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119435"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Utilizar módulos para incluir archivos en la solución
  Puede haber ocasiones cuando es posible que desee implementar archivos en el servidor de SharePoint independientemente de su tipo de archivo, como las nuevas páginas principales. Para ello, puede usar *módulos* (para que no se debe confundir con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] los módulos de código). Los módulos son contenedores de archivos en una solución de SharePoint. Cuando se implementa la solución, se copian los archivos del módulo en las carpetas especificadas en el servidor de SharePoint.  
  
## <a name="module-items-and-elements"></a>Los elementos y elementos de módulo
 Para crear un módulo, agréguelo a un proyecto eligiendo en la **Agregar nuevo elemento** cuadro de diálogo. A continuación, modifique su *Elements.xml* archivo para incluir los nombres de los archivos que desea implementar, dónde se encuentran en el sistema, y donde se deben copiar en el servidor de SharePoint.  
  
 Este es un ejemplo de la *Elements.xml* archivo de un módulo:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Acaba de crear módulos contienen los archivos predeterminados siguientes:  
  
|Nombre de archivo|Descripción|  
|---------------|-----------------|  
|*Elements.Xml*|El archivo de definición del módulo.|  
|*Sample.txt*|Un archivo de marcador de posición que actúa como un ejemplo de un archivo en el módulo.|  
  
 El *Elements.xml* archivo contiene los siguientes elementos:  
  
|Nombre del elemento|Descripción|  
|------------------|-----------------|  
|Elementos|Contiene todos los elementos definidos en el módulo.|  
|Module|El elemento de módulo tiene un atributo único, *nombre*, que especifica el nombre del módulo en el formato `<Module Name="Module1">`.<br /><br /> Tenga en cuenta que si cambia el nombre del módulo (o su *nombre de la carpeta* propiedad), debe actualizar manualmente el nombre del elemento de módulo.<br /><br /> Si especifica un subdirectorio para los archivos en el elemento de módulo, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) creará automáticamente una estructura de directorios coincidentes para ellos.|  
|Archivo|El elemento del archivo tiene dos parámetros, *ruta* y *Url*.<br /><br /> -Ruta de acceso: El nombre y la ubicación del archivo en la solución de SharePoint. El formato es, `Path="Module1\Sample.txt"`.<br /><br /> -Dirección Url: La ubicación donde se implementará el archivo en el servidor de SharePoint. El formato es, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Un atributo opcional que tiene dos configuraciones: *GhostableInLibrary* y *Ghostable*. El formato es, `Type="GhostableInLibrary"`. Especificar *GhostableInLibrary* significa que el archivo se agregará a una biblioteca de documentos de SharePoint junto con un elemento de lista para acompañar el archivo cuando se agrega a la biblioteca. Especificar *Ghostable* hace que el archivo se agrega a SharePoint fuera de la biblioteca de documentos.|  
  
 Cada archivo que desea implementar requiere otro `<File>` entrada de elemento en *Elements.xml*.  
  
## <a name="see-also"></a>Vea también
 [Cómo: incluir archivos mediante un módulo](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [Cómo: proporcionar un archivo](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
