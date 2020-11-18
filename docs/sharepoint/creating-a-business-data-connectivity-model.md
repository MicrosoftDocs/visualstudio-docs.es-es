---
title: Crear un modelo de conectividad a datos profesionales | Microsoft Docs
description: Cree un modelo de conectividad a datos profesionales (BDC) o personalice un modelo BDC existente mediante Visual Studio. Cada proyecto de SharePoint solo puede contener un modelo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0486ce6ac53850b1b607f9e7f859806cdc3ef8fe
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850473"
---
# <a name="create-a-business-data-connectivity-model"></a>Creación de un modelo de conectividad a datos profesionales
  Puede crear un modelo de conectividad a datos profesionales (BDC) o personalizar un modelo BDC existente mediante Visual Studio. Cada proyecto de SharePoint solo puede contener un modelo. Para obtener más información, vea [integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Creación de un modelo nuevo
 Para crear un nuevo modelo, cree un proyecto de **modelo de conectividad** a datos profesionales o agregue un elemento de modelo de **conectividad a datos profesionales** a un **proyecto de SharePoint vacío**.

> [!NOTE]
> Debe tener [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] instalado en el equipo.

 Visual Studio agrega una carpeta al proyecto. Esta carpeta tiene el nombre que especifica para el elemento **modelo de conectividad a datos profesionales** en el cuadro de diálogo **Agregar nuevo elemento** . Si crea un nuevo proyecto de **modelo de conectividad a datos profesionales** , Visual Studio asigna a la carpeta el nombre **BdcModel1**.

 Visual Studio agrega los siguientes archivos a la nueva carpeta:

|Archivo|Descripción|
|----------|-----------------|
|Archivo de definición de modelo|Contiene XML que define las entidades, los métodos, los objetos del sistema de línea de negocio (LOB) y otros metadatos que describen el modelo.<br /><br /> Modifique los metadatos de este archivo mediante el diseñador de BDC, el **Explorador** de BDC, la ventana **detalles del método de BDC** y la ventana **propiedades** .|
|Archivo de código de Entity Service|Contiene métodos que recuperan, actualizan y eliminan instancias de la entidad predeterminada.|

 Para definir las propiedades de una entidad, edite el archivo de código de entidad. Para obtener más información, vea [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Para recuperar, actualizar y eliminar instancias de una entidad, agregue código al archivo de código de Entity Service. Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

 Al compilar el proyecto, Visual Studio crea un ensamblado. Asegúrese de no agregar otros elementos al proyecto que agreguen código al ensamblado del proyecto (por ejemplo: un elemento de **flujo de trabajo secuencial** o un elemento de elemento **Web** ). El código de ese elemento no se ejecutará al implementar la solución porque el paquete de la solución no copia el ensamblado en la caché global de ensamblados.  El paquete de solución implementa el ensamblado en la base de datos de BDC solo en SharePoint.

> [!NOTE]
> Visual Studio copia el ensamblado en ambas ubicaciones del equipo local al depurar el proyecto.

## <a name="add-an-existing-model"></a>Agregar un modelo existente
 Puede importar un modelo creado con otras herramientas como SharePoint Designer. Puede optar por importar un modelo existente en el proyecto en las siguientes situaciones:

- Para personalizar un modelo que ya está implementado en una granja de servidores de SharePoint.

- Para empaquetar e implementar un modelo existente en varias granjas de servidores de SharePoint.

  En cualquier caso, los sistemas LOB definidos en el modelo que se importan no se ven afectados y seguirán funcionando según lo previsto. Para agregar un modelo existente a un proyecto de SharePoint, use el cuadro de diálogo **Agregar elemento existente** de Visual Studio. Para obtener más información, vea [Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Puede Agregar un sistema LOB de tipo .NET Framework ensamblado al modelo importado seleccionando una opción en el **LobSystem agregar ensamblado .net**. Esto le permite escribir código personalizado y utilizar un diseñador para definir los metadatos para el modelo importado.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: para crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)|Muestra cómo crear un nuevo modelo BDC.|
|[Cómo: para agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Muestra cómo importar un modelo existente en un proyecto de SharePoint.|
|[Cómo: para usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Describe cómo proporcionar cadenas que se combinan con los metadatos del modelo cuando un elemento Web o una página web consume el modelo.|
|[Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Muestra cómo incluir un ensamblado personalizado en la característica.|
