---
title: 'Cómo: Crear un modelo de BDC | Microsoft Docs'
description: Cree un modelo de conectividad de datos empresariales (BDC) mediante la plantilla Visual Studio para ese tipo de elemento y, a continuación, agregue el modelo a cualquier proyecto de SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112406"
---
# <a name="how-to-create-a-bdc-model"></a>Cómo: para crear un modelo BDC

  Puede crear un modelo de conectividad de datos empresariales (BDC) mediante la plantilla para ese tipo de elemento y, a continuación, agregando el modelo a cualquier proyecto de SharePoint. Para obtener más información, vea [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md). Para obtener más información sobre cómo diseñar el modelo, vea [Diseño de un modelo de conectividad de datos empresariales.](../sharepoint/designing-a-business-data-connectivity-model.md)

## <a name="to-create-a-bdc-project"></a>Para crear un proyecto de BDC

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.
::: moniker range="=vs-2017"
   > [!NOTE]
   > Si el IDE está configurado para usar Visual Basic de desarrollo, elija **Archivo**  >  **nuevo proyecto.**

  Aparece el cuadro de diálogo **Nuevo proyecto** .

2. En **Visual Basic** o **Visual C#,** elija **Office/SharePoint,** **Soluciones de SharePoint.**

3. En el **panel** Plantillas, elija el elemento **SharePoint 2013 - Proyecto** vacío y, a continuación, elija el **botón** Aceptar.

     Se **abre el Asistente para personalización de SharePoint.**
::: moniker-end
::: moniker range=">=vs-2019"
2. En el **cuadro de diálogo Crear** un nuevo proyecto, seleccione el proyecto vacío de *SharePoint** para la versión concreta de SharePoint que ha instalado. Por ejemplo, si tiene la instalación de SharePoint 2019, seleccione la plantilla **SharePoint 2019 - Proyecto vacío.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Cambie el nombre del proyecto si lo desea y, a continuación, elija el **botón** Crear.

::: moniker-end
4. En  la página Especificar el sitio y el nivel de seguridad para la depuración, especifique la dirección URL de  un sitio de SharePoint en el equipo local, elija el botón de opción Implementar como solución de granja y, a continuación, elija el botón Finalizar. 

     Probará el modelo en el sitio de SharePoint que especificó.

    > [!IMPORTANT]
    > Debe implementar el proyecto como una solución de granja porque los modelos de BDC solo admiten soluciones de granja.

     Se crea un proyecto de SharePoint vacío.

5. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

6. En el **cuadro de diálogo Agregar nuevo** elemento, elija el nodo **Office/SharePoint.**

7. En la lista de plantillas de SharePoint, elija **Modelo de conectividad de datos empresariales (solo solución de granja de servidores).**

8. En el **cuadro** Nombre , especifique un nombre para el modelo de BDC y, a continuación, elija el **botón** Agregar.

     Se **agrega un elemento Modelo** de conectividad de datos empresariales al proyecto. De forma predeterminada, el modelo aparece en el diseñador de BDC. Para obtener más información, vea [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Vea también

- [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Cómo: para agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Cómo: para usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integración de datos empresariales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
