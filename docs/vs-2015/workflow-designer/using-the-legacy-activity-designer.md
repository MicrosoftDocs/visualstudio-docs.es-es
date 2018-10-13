---
title: Usar el Diseñador de actividad Legacy | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 4c71fa8d901653babd8c3558da7eff8ff16058c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296834"
---
# <a name="using-the-legacy-activity-designer"></a>Usar el diseñador de actividad Legacy
En este tema se describe cómo usar el diseñador de actividad en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el diseñador heredado cuando tenga como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 El diseñador de actividades le permite crear sus propias actividades personalizadas.  
  
## <a name="creating-a-custom-activity"></a>Crear una actividad personalizada  
 Siga estos pasos para crear una actividad personalizada con el diseñador de actividades:  
  
1.  En el **proyecto** menú, haga clic en **agregar actividad**.  
  
2.  Seleccione el **actividad** o **Activity (con separación de código)** plantilla.  
  
    1.  Use la **actividad** plantilla para crear una actividad con la definición de actividad y el código de usuario en el mismo archivo de código.  
  
    2.  Use la **Activity (con separación de código)** plantilla para crear una actividad con la definición de actividad expresada como marcado de flujo de trabajo y el código de usuario en un archivo de código independiente.  
  
3.  Escriba un nombre de actividad o mantenga el nombre predeterminado y, a continuación, haga clic en **agregar**.  
  
 También puede crear un conjunto de actividades personalizadas creando un nuevo proyecto de tipo **Workflow Activity Library**. Para obtener más información acerca de este tipo de proyecto, vea [Cómo: crear una biblioteca de actividades de flujo de trabajo (heredado)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## <a name="configuring-an-activity"></a>Configurar una actividad  
 Aunque el diseñador de actividades esté activo, puede utilizar el explorador de propiedades para configurar las propiedades enumeradas en la siguiente tabla.  
  
|Propiedad|Comentarios|  
|--------------|--------------|  
|**Name**|Nombre de la actividad.|  
|**Clase base**|Clase base de la que deriva la actividad. La clase base predeterminada es [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). En el **propiedades** ventana, haga clic en el **clase Base** elipses **[...]**  para seleccionar otra clase base en el [examinar y seleccionar un cuadro de diálogo de tipo .NET (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Descripción**|Descripción de la actividad definida por el usuario.|  
|**Habilitado**|Establecido en **True** de forma predeterminada para habilitar la validación y ejecución de la actividad. Establecido en **False** para deshabilitar la validación y ejecución de la actividad. Para obtener información sobre la ejecución de actividad y la validación, consulte [desarrollar actividades de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## <a name="adding-child-activities"></a>Agregar actividades secundarias  
 Puede arrastrar actividades secundarias del cuadro de herramientas hasta la actividad que esté diseñando. Puede configurar cada una de las actividades secundarias con el explorador de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar actividades de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Crear actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Actividades de flujo de trabajo heredado](../workflow-designer/legacy-workflow-activities.md)   
 [Ejemplos de actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Cómo: crear una biblioteca de actividades de flujo de trabajo (heredado)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Usar el Diseñador de flujo de trabajo heredado](../workflow-designer/using-the-legacy-workflow-designer.md)