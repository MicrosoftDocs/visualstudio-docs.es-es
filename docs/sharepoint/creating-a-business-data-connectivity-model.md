---
title: Creación de un modelo de conectividad a datos empresariales | Microsoft Docs
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2a1feefe5bc338460f359dd6c1a25b50bddf67ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957490"
---
# <a name="create-a-business-data-connectivity-model"></a>Crear un modelo de conectividad a datos empresariales
  Puede crear un modelo de conectividad de datos profesionales (BDC) o personalizar un modelo BDC existente mediante Visual Studio. Cada proyecto de SharePoint puede contener un único modelo. Para obtener más información, consulte [integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="create-a-new-model"></a>Crear un nuevo modelo
 Para crear un nuevo modelo, cree un **modelo de conectividad a datos empresariales** proyecto o agregue un **modelo de conectividad a datos empresariales** elemento a una **proyecto vacío de SharePoint**.  
  
> [!NOTE]  
>  Debe tener [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] instalado en el equipo.  
  
 Visual Studio agrega una carpeta al proyecto. Esta carpeta tiene el nombre que especifique para la **modelo de conectividad a datos empresariales** de elemento en el **Agregar nuevo elemento** cuadro de diálogo. Si crea un nuevo **modelo de conectividad a datos empresariales** proyecto, Visual Studio asigna a la carpeta **BdcModel1**.  
  
 Visual Studio agrega los siguientes archivos a la nueva carpeta:  
  
|Archivo|Descripción|  
|----------|-----------------|  
|Archivo de definición de modelo|Contiene el XML que define las entidades, métodos, objetos del sistema de línea de negocio (LOB) y otros metadatos que describen el modelo.<br /><br /> Modificar los metadatos de este archivo mediante el Diseñador de BDC, **Explorador de BDC**, **detalles del método de BDC** ventana, y **propiedades** ventana.|  
|Archivo de código del servicio de entidad|Contiene métodos que recuperarán, actualización y eliminan instancias de la entidad de forma predeterminada.|  
  
 Para definir las propiedades de una entidad, edite el archivo de código de la entidad. Para obtener más información, vea [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Para recuperar, actualizar y eliminar instancias de una entidad, agregue código al archivo de código del servicio de entidad. Para obtener más información, consulte [diseñar un modelo de conectividad de datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Al compilar el proyecto, Visual Studio crea un ensamblado. Asegúrese de no agregar otros elementos al proyecto que agregue código al ensamblado del proyecto (por ejemplo: un **flujo de trabajo secuencial** elemento o un **elemento Web** elemento). El código para ese elemento no se ejecutará al implementar la solución porque el paquete de solución no copia el ensamblado en la caché global de ensamblados.  El paquete de solución implementa el ensamblado para el BDC sólo base de datos en SharePoint.  
  
> [!NOTE]  
>  Visual Studio copia el ensamblado en ambas ubicaciones en el equipo local cuando se depura el proyecto.  
  
## <a name="add-an-existing-model"></a>Agregar un modelo existente
 Puede importar un modelo que se creó con otras herramientas, como SharePoint Designer. Es posible que elija importar un modelo existente al proyecto en las situaciones siguientes:  
  
- Para personalizar un modelo que se ha implementado en una granja de servidores de SharePoint.  
  
- Para empaquetar e implementar un modelo existente en varias granjas de servidores de SharePoint.  
  
  En cualquier caso, definidos en el modelo que se importa los sistemas de LOB no se ven afectados y seguirán funcionando según lo previsto. Para agregar un modelo existente a un proyecto de SharePoint, use Visual Studio **Agregar elemento existente** cuadro de diálogo. Para obtener más información, vea [Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
  Puede agregar un sistema LOB de ensamblado del tipo de .NET Framework para el modelo importado seleccionando una opción en el **LobSystem de ensamblado .NET agregar**. Esto le permite escribir código personalizado y usar un diseñador para definir los metadatos del modelo importado.  
  
## <a name="related-topics"></a>Temas relacionados
  
|Título|Descripción|  
|-----------|-----------------|  
|[Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)|Muestra cómo crear un nuevo modelo BDC.|  
|[Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Muestra cómo importar un modelo existente a un proyecto de SharePoint.|  
|[Cómo: Use un archivo de recursos para especificar los permisos, propiedades y nombres localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Describe cómo proporcionar cadenas que se combinan con los metadatos del modelo cuando se consume el modelo de un elemento Web o una página Web.|  
|[Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Muestra cómo incluir un ensamblado personalizado en la característica.|  
