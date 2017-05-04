---
title: "Crea un modelo de conectividad a datos profesionales | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], crear un modelo"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], crear un modelo"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], modelo"
  - "desarrollo de SharePoint en Visual Studio, servicio de conectividad a datos profesionales"
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Crea un modelo de conectividad a datos profesionales
  Puede crear un modelo de Conectividad a datos profesionales \(BDC\) o personalizar un modelo BDC existente con Visual Studio.  Cada proyecto de SharePoint solo puede contener un modelo.  Para obtener más información, vea [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Crear un nuevo modelo  
 Para crear un nuevo modelo, cree un proyecto de **Modelo de conectividad a datos profesionales** o agregue un elemento **Modelo de conectividad a datos profesionales** a un **Proyecto de SharePoint vacío**.  
  
> [!NOTE]  
>  Debe tener [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] instalado en el equipo.  
  
 Visual Studio agrega una carpeta al proyecto.  Esta carpeta tiene el nombre especificado para el elemento **Modelo de conectividad a datos profesionales** en el cuadro de diálogo **Agregar nuevo elemento**.  Si crea un nuevo proyecto de **Modelo de conectividad a datos profesionales**, Visual Studio denomina la carpeta **BdcModel1**.  
  
 Visual Studio agrega los siguientes archivos a la nueva carpeta:  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|Archivo de definición del modelo|Contiene XML que define las entidades, los métodos, los objetos de sistema de Línea de negocio \(LOB\) y otros metadatos que describen el modelo.<br /><br /> Modifique los metadatos en este archivo con las ventanas Diseñador de BDC, **Explorador de BDC**, **Detalles del método de BDC** y **Propiedades**.|  
|Archivo de código del servicio de entidad|Contiene métodos que recuperan, actualizan y eliminan instancias de la entidad predeterminada.|  
  
 Para definir las propiedades de una entidad, modifique el archivo de código de la entidad.  Para obtener más información, vea [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Para recuperar, actualizar y eliminar instancias de una entidad, agregue código al archivo de código del servicio de entidad.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Al compilar el proyecto, Visual Studio crea un ensamblado.  Asegúrese de que no agrega otros elementos que agreguen código al ensamblado del proyecto \(por ejemplo: un elemento **Flujo de trabajo secuencial** o un elemento de **elemento web**\).  El código para ese elemento no se ejecutará al implementar la solución porque el paquete de la solución no copia el ensamblado en la memoria caché global de ensamblados.  El paquete de la solución solo implementa el ensamblado en la base de datos de BDC en SharePoint.  
  
> [!NOTE]  
>  Visual Studio copia el ensamblado en ambas ubicaciones del equipo local al depurar el proyecto.  
  
## Agregar un modelo existente  
 Puede importar un modelo creado con otras herramientas, por ejemplo, el Diseñador de SharePoint.  Puede resultar interesante importar un modelo existente al proyecto en las siguientes situaciones:  
  
-   Para personalizar un modelo que ya se he implementado en una granja de servidores de SharePoint.  
  
-   Para empaquetar e implementar un modelo existente en varias granjas de servidores de SharePoint.  
  
 En cualquier caso, los sistemas LOB definidos en el modelo que usted importa no se ven afectados y seguirán funcionando del modo esperado.  Para agregar un modelo existente a un proyecto de SharePoint, utilice el cuadro de diálogo de Visual Studio **Agregar elemento existente**.  Para obtener más información, vea [Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 Puede agregar un sistema LOB del tipo ensamblado de .NET Framework al modelo importado seleccionando una opción en **Agregar LobSystem de ensamblado .NET**.  Esto lo permite escribir código personalizado y utilizar un diseñador para definir los metadatos del modelo importado.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)|Muestra cómo crear un nuevo modelo BDC.|  
|[Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Muestra cómo importar un modelo existente en un proyecto SharePoint.|  
|[Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Describe cómo proporcionar cadenas que están combinadas con metadatos del modelo cuando un elemento web o página web utiliza el modelo.|  
|[Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Muestra cómo incluir un ensamblado personalizado en la característica.|  
  
  