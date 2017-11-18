---
title: "Utilizar el Diseñador de actividades heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 65510d727fdf0640ca8efa646a14d0814951cd4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-legacy-activity-designer"></a>Usar el diseñador de actividad Legacy
En este tema se describe cómo usar el diseñador de actividad en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado. Use el diseñador heredado cuando tenga como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 El diseñador de actividades le permite crear sus propias actividades personalizadas.  
  
## <a name="creating-a-custom-activity"></a>Crear una actividad personalizada  
 Siga estos pasos para crear una actividad personalizada con el diseñador de actividades:  
  
1.  En el **proyecto** menú, haga clic en **agregar actividad**.  
  
2.  Seleccione el **actividad** o **Activity (con separación de código)** plantilla.  
  
    1.  Use la **actividad** plantilla para crear una actividad con la definición de actividad y el código de usuario en el mismo archivo de código.  
  
    2.  Use la **Activity (con separación de código)** plantilla para crear una actividad con la definición de actividad expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.  
  
3.  Escriba un nombre de actividad o mantenga el nombre predeterminado y, a continuación, haga clic en **agregar**.  
  
 También puede crear un conjunto de actividades personalizadas creando un nuevo proyecto de tipo **biblioteca de actividades de flujo de trabajo**. Para obtener más información acerca de este tipo de proyecto, vea [Cómo: crear una biblioteca de actividades de flujo de trabajo (heredado)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## <a name="configuring-an-activity"></a>Configurar una actividad  
 Aunque el diseñador de actividades esté activo, puede utilizar el explorador de propiedades para configurar las propiedades enumeradas en la siguiente tabla.  
  
|Propiedad|Comentarios|  
|--------------|--------------|  
|**Nombre**|Nombre de la actividad.|  
|**Clase base**|Clase base de la que deriva la actividad. La clase base predeterminada es [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). En el **propiedades** ventana, haga clic en el **una clase Base** puntos suspensivos **[...]**  para seleccionar otra clase base en el [examinar y seleccionar un cuadro de diálogo de tipo de .NET (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Descripción**|Descripción de la actividad definida por el usuario.|  
|**Habilitado**|Establecido en **True** de forma predeterminada para habilitar la ejecución de la actividad y validación. Establecido en **False** para deshabilitar la ejecución de la actividad y validación. Para obtener información sobre la ejecución de la actividad y la validación, consulte [desarrollar actividades de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## <a name="adding-child-activities"></a>Agregar actividades secundarias  
 Puede arrastrar actividades secundarias del cuadro de herramientas hasta la actividad que esté diseñando. Puede configurar cada una de las actividades secundarias con el explorador de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar actividades de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Crear actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Actividades de flujo de trabajo heredado](../workflow-designer/legacy-workflow-activities.md)   
 [Ejemplos de actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Cómo: crear una biblioteca de actividades de flujo de trabajo (heredado)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Usar el Diseñador de flujo de trabajo heredado](../workflow-designer/using-the-legacy-workflow-designer.md)