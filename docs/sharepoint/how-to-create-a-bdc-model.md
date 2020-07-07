---
title: 'Cómo: crear un modelo BDC | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 139da31ced1d32def450a1dc176ca241b0c4677f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014538"
---
# <a name="how-to-create-a-bdc-model"></a>Cómo: crear un modelo BDC
  Puede crear un modelo de conectividad a datos profesionales (BDC) utilizando la plantilla para ese tipo de elemento y, a continuación, agregando el modelo a cualquier proyecto de SharePoint. Para obtener más información, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md). Para obtener más información sobre cómo diseñar el modelo, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>Para crear un proyecto de BDC

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

    > [!NOTE]
    > Si el IDE está establecido para usar la configuración de desarrollo de Visual Basic, elija **archivo**  >  **nuevo proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

2. En **Visual Basic** o **Visual C#**, elija **Office/SharePoint**, soluciones de **SharePoint**.

3. En el panel **plantillas** , elija el elemento de **proyecto SharePoint 2013-vacío** y, a continuación, elija el botón **Aceptar** .

     Se abre el **Asistente para la personalización de SharePoint** .

4. En la página **especificar el sitio y el nivel de seguridad de la depuración** , especifique la dirección URL de un sitio de SharePoint en el equipo local, elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **Finalizar** .

     Probará el modelo en el sitio de SharePoint que especificó.

    > [!IMPORTANT]
    > Debe implementar el proyecto como una solución de granja de servidores, ya que los modelos BDC solo admiten soluciones de granja.

     Se crea un proyecto de SharePoint vacío.

5. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

6. En el cuadro de diálogo **Agregar nuevo elemento** , elija el nodo **Office/SharePoint** .

7. En la lista de plantillas de SharePoint, elija **modelo de conectividad a datos profesionales (solo solución de granja de servidores)**.

8. En el cuadro **nombre** , especifique un nombre para el modelo BDC y, a continuación, elija el botón **Agregar** .

     Se agrega al proyecto un elemento de **modelo de conectividad a datos profesionales** . De forma predeterminada, el modelo aparece en el diseñador de BDC. Para obtener más información, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Consulte también
- [Crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Cómo: usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
